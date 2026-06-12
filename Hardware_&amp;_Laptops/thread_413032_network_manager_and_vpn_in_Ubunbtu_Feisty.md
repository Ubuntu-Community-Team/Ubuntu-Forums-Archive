---
title: "network manager and vpn in Ubunbtu Feisty"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by analyzer123 on 2007-04-18
Hi, 
I just installed Ubuntu Feisty (alternate CD) on my dell E1405. My experience has been OK, nothing really great. I am having major problems with 3 things:

1. The network manager applet - I finally got the wireless going after following the instructions in this forum. The wifi is working fine, the only problem is that the applet in the notification area onyl displays the 2 screens icon, and not the wireless bars icon with the bars. When i move between networks, I should be able to graphically see a list of networks and easily select the correct one, but when i click on this applet I only see "manual configuration"
My "wired' network is turned off. If I actually go into the manual configuration mode and click on edit preferences, I can indeed see the list of wifi nodes around, but I want to see them without all this hassle.
Any idea how I can make the icon display wireless nodes and signal strength?

2. cisco VPN - this is really buggy in linux. My problem is - I want to be able to select if I want to use VPN or no, and if yes then which profile. But its clumsy not having a GUI. I tried using the gvpndialer gui but its not compiling correctly.

3. The synaptics touchpad - the touchpad itself is working fine, but I am not happy with the single click sensitivity of the touchpad - i feel I am having to hit it down harder than I do in XP. Any GUI which allows me to adjust settings like in XP?

Thanks.
- A

---

### Post by feranick on 2007-04-18
Why don't you use vpnc, the free implementation of the Cisco VPN?. It's in the repositories:

sudo apt-get install vpnc.

Examples of configuration files are in /etc/vpnc

---

### Post by GargoyleMusic on 2007-04-20
Try installing network-manager-vpnc - it is a plugin for network-manager. I think it also installs vpnc.

(I don't know if this actually works, but its definitely worth a shot)

---

### Post by analyzer123 on 2007-04-20
how do i get the wireless bars icon there? I am not able to easily switch between networks.

---

