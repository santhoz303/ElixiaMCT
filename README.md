CREATE USER localelixiauser WITH password 'leu2025)!';

	CREATE DATABASE elixialocaldb;

	GRANT ALL PRIVILEGES ON DATABASE elixialocaldb TO localelixiauser;

	\c elixialocaldb
	GRANT ALL on SCHEMA public to localelixiauser;

	\c postgres
	GRANT ALL PRIVILEGES ON DATABASE elixialocaldb TO localelixiauser;
 
cd  “project directory”

dotnet tool install --global dotnet-ef
dotnet tool update --global dotnet-ef

dotnet add package Microsoft.EntityFrameworkCore.Design

dotnet ef migrations add InitialCreate --context ApplicationDbContext 

dotnet ef database update --context ApplicationDbContext 
If we need to generate a script in sql query (.sql) and  If we are Using the context folder in different project - use this below command after Intialcreate done.

dotnet ef migrations script --context ElixiaDbContext -o DbScripts\FullDbScript.sql
