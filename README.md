# How to configure Client-side Blazor v.3.0.0 Preview 6 that is hosted on an ASP.NET Core server to deploy it to Azure? (at 13 Jul, 2019)

## Summary

This sample code describe about how to configure Client-side Blazor v.3.0.0 Preview 6 that is hosted on an ASP.NET Core server to deploy it to Azure Web App.

This sample code treat the scenario that publish from Visual Studio 2019 v.16.2 Preview 3 by "Web Deploy" manually.

## Issues at this time (13 Jul, 2019)

- Azure Web App doesn't include .NET Core 3.0 Preview 6 runtime.
- The publishing process to the Azure Web App from Visual Studio will fail with the error below: 

> "Assets file '...Client\obj\project.assets.json' doesn't have a target for '.NETStandard,Version=v2.0'. Ensure that restore has run and that you have included 'netstandard2.0' in the TargetFrameworks for your project."
- The web root content of the Blazor Client project is not copied directly under the "wwwroot" folder.

I think these issues will be fixed in the future.

## How to avoid those issues?

- Configure the publish profile to "Self-contain" deployment mode.
- Edit all .csproj files to change `<TargetFramework>...</TargetFramework>` node name to `<TargetFrameworks>...</TargetFrameworks>`. (see also: [https://stackoverflow.com/a/42855070](https://stackoverflow.com/a/42855070) ) (commit: [8513775](https://github.com/sample-by-jsakamoto/BlazorHostedV3Preview6OnAzureWebApp/commit/851377501e53dac91b6f7379cc043144180315d8))
- Fix the web root folder path string at runtime in `Startup` class. (commit: [5c3dcb9](https://github.com/sample-by-jsakamoto/BlazorHostedV3Preview6OnAzureWebApp/commit/5c3dcb9219fa75c05d6911ba6d7e40ff9ed8d949))

## License

[The Unlicense](LICENSE)
