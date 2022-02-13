FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish Admin.csproj -c Release -o publish
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
COPY --from=build /app/publish . 
ENV ASPNETCORE_URLS="http://*:80"
ENTRYPOINT ["dotnet", "Admin.dll"]
