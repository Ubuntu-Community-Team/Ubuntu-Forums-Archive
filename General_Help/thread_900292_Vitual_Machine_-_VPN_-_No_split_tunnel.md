---
title: "Vitual Machine - VPN - No split tunnel"
date: 2008-08-25
forum: General Help
---

### Post by blacklobo on 2008-08-25
**Problem:**
I cannot connect to the VPN with a Virtual Machine.  _The VPN does not allow split tunneling._



**Here is the setup:**
- PC with Ubuntu 8.04
- VMware server 1.0.6 build-91891
- Virtual Machine with Ubuntu 8.04
- Cisco Systems VPN Client Version 4.8.01 (0640) Installed on both the host and virtual machine

**What does work:**
I can connect to the VPN through the host machine.  I can connect to the Internet from either machine when not VPNed in.  I can traceroute to the VPN destination from both the host and virtual machine.

**Additional Information:**
I have tried both bridge networks & NATed networks for the Virtual Machine.

---

### Post by linux_tech on 2008-08-25
What is the os on host and guest?
Is the guest and host os firewall off? I would turn both off for now 

you can add port-
netsh fi add port UDP 62515 "Cisco VPN Service" enable all

Did you select Enable Transparent Tunneling check box
and  IPSec over TCPand put 443 in the port field

Are there 2 network adapters in the pc or 1?   What type of router are you using? Are you using pptp or ipsec?  

Have you tried reinstalling the client?

download -
[http://www.colorado.edu/ITS/vpn/clients.html](http://www.colorado.edu/ITS/vpn/clients.html)

more instructions here [https://net.tamu.edu/network/vpn/vpn.html](https://net.tamu.edu/network/vpn/vpn.html)

---

### Post by blacklobo on 2008-08-26
> **linux_tech said:**
> What is the os on host and guest?
Is the guest and host os firewall off? I would turn both off for now 

you can add port-
netsh fi add port UDP 62515 "Cisco VPN Service" enable all

Did you select Enable Transparent Tunneling check box
and  IPSec over TCPand put 443 in the port field

Are there 2 network adapters in the pc or 1?   What type of router are you using? Are you using pptp or ipsec?  

Have you tried reinstalling the client?


[LIST]
[*]I have not enabled a firewall in either Ubuntu system.
[*]"netsh" is not installed.
[*]The linux VPN client is not GUI based so there was no check box to click.  From looking at the pcf files I don't see that as an available option.
[*]Both the Host & virtual OS are Ubuntu 8.04.
[*]To the best of my knowledge there is no newer client for a Linux OS than  4.8.01.
[*]I only have 1 network adapter installed.
[*]IPSec is used
[/LIST]

---

### Post by de0xyrib0se on 2008-08-26
Explain what exactly you cant do, you cannot connect to the VPN or you cant do a split?

Also it is pointless using their command line client when there is a  VPNC client which also has a network-manager admin plug-in.

---

