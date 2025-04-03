<!-- markdownlint-disable MD033 -->
<h1 align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/sighupio/distribution/refs/heads/main/docs/assets/white-logo.png">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/sighupio/distribution/refs/heads/main/docs/assets/black-logo.png">
  <img alt="Shows a black logo in light color mode and a white one in dark color mode." src="https://raw.githubusercontent.com/sighupio/distribution/refs/heads/main/docs/assets/white-logo.png">
</picture><br/>
  AKS Installer
</h1>
<!-- markdownlint-enable MD033 -->

![Release](https://img.shields.io/github/v/release/sighupio/installer-aks?label=Latest%20Release)
![License](https://img.shields.io/github/license/sighupio/installer-aks?label=License)
[![Slack](https://img.shields.io/badge/slack-@kubernetes/fury-yellow.svg?logo=slack&label=Slack)](https://kubernetes.slack.com/archives/C0154HYTAQH)

<!-- <SD-DOCS> -->

**AKS Installer** deploys a production-grade SIGHUP Distribution cluster on Azure Kubernetes Service (AKS).

If you are new to SIGHUP Distribution please refer to the [official documentation][sd-docs] on how to get started.

## Modules

The installer is composed of four terraform modules:

|            Module             |                       Description                      |
| ----------------------------- | ------------------------------------------------------ |
| [VNet][vnet-module]           | Deploy the necessary networking infrastructure         |
| [VPN][vpn-module]             | Deploy the a VPN Server to connect to private clusters |
| [AKS][aks-module]             | Deploy the AKS cluster                                 |
| [State][state-module]         | Deploy the Backend for Terraform State                 |

Click on each module to see its full documentation.

## Architecture

The [AKS module][aks-module] deploys an **AKS** cluster.

The [VNet module][vnet-module] setups all the necessary networking infrastructure.

The [VPN module][vpn-module] setups one or more bastion hosts with an OpenVPN server.

The bastion host includes an OpenVPN instance easily manageable by using [furyagent][furyagent] to provide access to the cluster.

> 🕵🏻‍♂️ [Furyagent][furyagent] is a tool developed by SIGHUP to manage OpenVPN and SSH user access to the bastion host.

## Usage

### Requirements

- **Azure CLI** >= `2.48.1`
- **Azure** account with enough permission to create an AKS Cluster.
- **terraform** = `>=1.3.0`
- `ssh` or **OpenVPN Client** - [Tunnelblick][tunnelblick] (on macOS) or [OpenVPN Connect][openvpn-connect] (for other OS) are recommended.

### Create AKS Cluster

To create the cluster via the installers:

1. (optional) Use the [State module][state-module] to deploy the storage account and container to store terraform state

2. Use the [VNet module][vnet-module] to deploy the networking infrastructure

3. (optional) Use the [VPN module][vpn-module] to deploy the openvpn bastion host

4. (optional) Configure access to the OpenVPN instance of the bastion host via [furyagent][furyagent]

5. (optional) Connect to the OpenVPN instance

6. Use the [AKS module][aks-module] to deploy the AKS cluster

Please refer to each module documentation and the [examples](examples/) folder for more details.

## Useful links

- [AKS pricing](https://azure.microsoft.com/en-us/pricing/details/kubernetes-service/)
- [Committed use Instances pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/linux/)
- [Identity in AKS](https://learn.microsoft.com/en-us/azure/aks/concepts-identity)

<!-- Links -->

[aks-installer-docs]: https://docs.kubernetesfury.com/docs/installers/managed/aks/
[aks-module]: https://github.com/sighupio/installer-aks/tree/master/modules/aks
[vnet-module]: https://github.com/sighupio/installer-aks/tree/master/modules/vnet
[vpn-module]: https://github.com/sighupio/installer-aks/tree/master/modules/vpn
[state-module]: https://github.com/sighupio/installer-aks/tree/master/modules/state
[sd-docs]: https://docs.kubernetesfury.com/docs/distribution/

[furyagent]: https://github.com/sighupio/furyagent
[tunnelblick]: https://tunnelblick.net/downloads.html
[openvpn-connect]: https://openvpn.net/vpn-client/

<!-- </SD-DOCS> -->
<!-- <FOOTER> -->

### Reporting Issues

In case you experience any problem with the module, please [open a new issue](https://github.com/sighupio/installer-aks/issues/new).

## License

This module is open-source and it's released under the following [LICENSE](LICENSE)

<!-- </FOOTER> -->
