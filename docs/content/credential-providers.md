# Paket support for Credential Providers

Paket supports Credential Providers through the same interface as [NuGet](https://docs.microsoft.com/en-us/nuget/reference/extensibility/nuget-exe-credential-providers).

## Development

For regular paket users installing Credential Providers works the same as for the NuGet client. If you have already installed Credential Providers in `%LOCALAPPDATA%\NuGet\CredentialProviders` paket should pick them up immediatly.

Example VSTS:

1. Download the credential providers from you VSTS Instance.
   ![VSTS Credential Providers](img/credential-providers-vsts.png)
2. Extract the `CredentialProvider.VSS.exe` file into the above path (`%LOCALAPPDATA%\NuGet\CredentialProviders`)
3. use paket normally (without password in `paket.dependencies` and config) and enter the password in the provided dialog.

## CI

There are two options to use Credential Providers in your build agent:

1. Either install a global Credential Provider on your agent
2. Use Tasks to provide Credential Providers as part of your build.

Example VSTS:

Install https://github.com/matthid/Paket.TeamBuildCredentials/releases/tag/0.1.1 on your TFS
Add the "Setup Paket credential manager" build step before calling Paket.
See more infos [here](https://github.com/matthid/Paket.TeamBuildCredentials)