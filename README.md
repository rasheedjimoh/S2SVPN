# Site-to-Site VPN(IPsec)

## Objective

The objective is to establish a secure Site-to-Site VPN connection between an on-premises network and Azure, facilitating seamless communication and data exchange between the two environments. This entails setting up a Virtual Network (VNet) in Azure, configuring a Local Network Gateway, provisioning necessary IP addresses, deploying a Virtual Network Gateway, and configuring the appropriate services on the Windows Server side to enable connectivity.

### Skills Learned

- **Azure Networking**: Understanding the setup and configuration of Virtual Networks (VNets), including subnetting and gateway subnet creation.
- **VPN Configuration**: Configuring a Site-to-Site VPN connection in Azure, including understanding VPN types and protocols such as IPsec.
- **Network Gateway Management**: Configuring and managing Local Network Gateways and Virtual Network Gateways in Azure.
- **Public IP Address Management**: Provisioning and managing Public IP addresses for Azure resources.
- **Windows Server Configuration**: Configuring roles and features on Windows Server, specifically Routing and Remote Access Services.
- **Demand-dial VPN Configuration**: Setting up and configuring Demand-dial VPN connections on Windows Server to establish connectivity with Azure VNets.
- **DHCP Scope Configuration**: Understanding and configuring DHCP scopes for LAN connectivity.
- **Networking Troubleshooting**: Troubleshooting connectivity issues between on-premises networks and Azure, including VPN connectivity problems.

### Tools Used

- **Azure Portal**: Utilized for provisioning and managing Azure resources such as Virtual Networks, Local Network Gateways, Virtual Network Gateways, and Public IP addresses.
- **Windows Server**: Deployed for configuring roles and features, specifically the Routing and Remote Access Service, to enable Demand-dial VPN connections to Azure VNets.
- **Networking Equipment**: Used to configure and manage on-premises network settings, including routers, switches, and firewalls, to facilitate the Site-to-Site VPN connection with Azure.
- **VPN Client Software**: Utilized for configuring and establishing the Demand-dial VPN connection from the Windows Server to the Azure Virtual Network.
- **DHCP Management Tools**: Employed for configuring DHCP scopes for LAN connectivity, ensuring proper IP address allocation within the on-premises network.
- **Network Troubleshooting Tools**: Used for diagnosing and troubleshooting connectivity issues between the on-premises network and Azure, including tools for monitoring VPN connections and network traffic.

## Steps

Here's a step-by-step process:

Step 1: **Setting Up the Azure Environment(Virtual network)**
Alright, first things first, let's head over to the Azure Portal. Once you're logged in, navigate to the Networking section and select Virtual Networks. Here, we'll create a new VNet. Click on "+ Create" and fill in the necessary details like the name and region. When creating the VNet, we'll define our private subnet (let's say 10.0.0.0/24) where our Azure resources will reside and a gateway subnet (let's use 10.0.1.0/28) which will be used for the VPN connection.


![image](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/0be2751e-fb34-433f-861a-9d1130c34309)



Step 2: **Configuring Local Network Gateway**
Now, let's set up our Local Network Gateway. This essentially represents our on-premises network in Azure. Go to the Networking section again and select Local Network Gateways. Click on "+ Create" and fill in the required details. This includes specifying your public IP address (the one your on-premises network is using) and your LAN DHCP scope information (like 172.16.0.0).

![image](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/2bb293b7-3039-4c7c-8d5f-4ebec6f11d77)


Step 3: **Provisioning Public IP Address**
Next, we need to provision a Public IP address for our Azure resources. This will be used for our Virtual Network Gateway. Simply go to Public IP addresses in the Networking section, click on "+ Create," and fill in the necessary details.

![Screenshot 2024-02-12 162156](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/96f6dcea-10af-48bd-bc1b-6b98cdb14155)


Step 4: **Deploying Virtual Network Gateway**
Now, let's set up our Virtual Network Gateway. This will handle the VPN connection between Azure and our on-premises network. Head over to Virtual Network Gateways in the Networking section, click on "+ Add," and fill in the required information. Make sure to select the correct VPN type, which in our case is Route-based.

![s2s-0](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/72f47ba1-d4ad-4f04-9aaf-120b16e7ecdd)


Step 5: **Configuring Windows Server**
Moving on to our on-premises side, we'll need to configure our Windows Server. We'll be using the Routing and Remote Access Service role. So, open up Server Manager, navigate to Add Roles and Features, select the Routing and Remote Access Service, and follow the wizard to install and configure it.

![RRAS](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/e8dc75a6-ee86-4f07-acbe-090f43213b8d)

-----

![RRAS-0](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/7dc2c9bc-bbe2-42f7-bca2-64ee73e8015c)

-----

![RRAS-1](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/89ab6276-9f19-4e14-b919-6546244406bf)

-----

![RRAS-2](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/d5888773-a6aa-47f3-92aa-4b8c7ae5f098)


-----


Step 6: **Establishing VPN Connection**
Lastly, let's establish the VPN connection from our Windows Server to Azure. Open up the Routing and Remote Access console on the Windows Server, navigate to Demand-dial Connections, click on "+ Add," and follow the wizard to configure the connection to our Azure Virtual Network (VNet).

![RRAS-3](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/097120c0-1ca0-40d8-ae3a-5916fdc12b89)


We've successfully set up a Site-to-Site VPN connection between our on-premises network and Azure.

![Screenshot 2024-02-12 160349](https://github.com/rasheedjimoh/S2SVPN/assets/157264080/e11a5370-a351-4f58-a95f-2086f2f37ee5)
*Ref 1: Site-to-Site VPN Connected successfully*
