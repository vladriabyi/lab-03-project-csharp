# Етап збірки
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

# Копіюємо файл проекту і відновлюємо залежності
COPY Program.csproj Program.csproj
RUN dotnet restore

# Копіюємо решту коду і збираємо проект
COPY Program.cs Program.cs
RUN dotnet build -c Release

# Етап створення runtime образу
FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/bin/Release/netcoreapp3.1 ./

# Вказуємо точку входу для додатку
ENTRYPOINT ["dotnet", "MyProgram.dll"]
