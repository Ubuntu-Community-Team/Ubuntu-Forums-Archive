---
title: "HP 530 Notebook NIC firmware problem (wireless works)"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by PrivateLifeOfPlants on 2007-12-27
[SIZE="3"]Hi, I'm new to Ubuntu (and Linux) so please go easy on me...

Computer: HP 530 Notebook
Intel PRO/100 VE Network Adapter Driver 
Broadcom 802.11b/g WLAN

Windows vista home basic / Ububtu 7.10 dual boot


Okay, heres what happened. I installed ubuntu from the live cd and when the installation was complete, ubuntu asked me if I wanted to allow proprietory firmware for the NIC or something and I must have pressed the wrong button.

I think I wiped the existing firmware from the NIC card. Nothing would come up under network for the wired network, but the wireless still works.

So, i rebooted back into Vista basic (OEM) and tried to reinstall the firmware from the HP website. I chose the correct model and everything. It didnt work.

So next i went onto Intel's website and got the appropriate driver from them and installed it.

Now, in Vista it kind of connects to the network (it says Unidentified network - local only, no internet) and in ubuntu it does nothing.


If it helps, heres what windows IPCONFIG gives me - 


Windows IP Configuration


Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Link-local IPv6 Address . . . . . : fe80::fcea:9c5b:6128:bcda%9
   IPv4 Address. . . . . . . . . . . : 192.168.2.12
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.2.1

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::d5ba:c572:a1eb:f735%8
   Autoconfiguration IPv4 Address. . : 169.254.247.53
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . : Belkin
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.2.12%11
   Default Gateway . . . . . . . . . :

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::5efe:169.254.247.53%12
   Default Gateway . . . . . . . . . :




A network diagnostic on the connection says:




This adapter is configured to obtain an 
IP address automatically. No DHCP Server is present
on the network. Windows selected an IP address using 
Alternate Private IP Addressing.

Ping Gateway 0.0.0.0 : Failed
No DNS Server available for this connection.
No WINS Server is available for this connection.
Ping DHCP 0.0.0.0 : Failed








I dont really know what to do next. As far as i know, all the other computers connected to the network are having no problems.




These are my router settings:



	
LAN Settings
	LAN/WLAN MAC 	00-30-BD-C9-99-20
	IP address 	192.168.2.1
  	Subnet mask 	255.255.255.0
  	DHCP Server 	Enabled
Internet Settings
	WAN MAC address 	00-30-BD-C9-99-21
  	Connection Type 	DYNAMIC
  	Subnet mask 	255.255.252.0
  	Wan IP 	82.12.156.146
  	Default gateway 	82.12.156.1
  	DNS Address 	194.168.4.100
	
Features
	NAT 	Enabled
  	Firewall Settings 	Enabled
  	SSID 	WLAN
  	Encryption 	Disable



Any help getting my NIC working again (e.g working firmware) for either vista / ubuntu would be appreciated.

Thank you.

[/SIZE]

---

