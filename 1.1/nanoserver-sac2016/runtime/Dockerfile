# escape=`
FROM microsoft/dotnet:1.1.9-runtime-nanoserver-sac2016

# set up network
ENV ASPNETCORE_URLS http://+:80

# set env var for packages cache
ENV DOTNET_HOSTING_OPTIMIZATION_CACHE C:/packagecache

# set up package caches
RUN @('1.1.0', '1.1.1', '1.1.2', '1.1.3', '1.1.4', '1.1.5', '1.1.6', '1.1.7', '1.1.8') | % { `
        $downloadUrl = \"https://dist.asp.net/packagecache/${_}/win7-x64/aspnetcore.cache.zip\"; `
        $fileName = \"cache${_}.zip\"; `
        Write-Host \"Downloading and extracting $downloadUrl\"; `
        Invoke-WebRequest $downloadUrl -OutFile $fileName; `
        Expand-Archive $fileName -DestinationPath ${env:DOTNET_HOSTING_OPTIMIZATION_CACHE}; `
        Remove-Item -Force $fileName `
    }
