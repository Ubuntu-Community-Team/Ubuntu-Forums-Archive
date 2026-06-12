---
title: "Help with setting up Wireless Connection Toshiba R100 laptop"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by khaledaboualfa on 2007-07-01
Okay the machine I'm trying to set it up on is a Toshiba laptop R100. The wireless card it's got is a PRO/Wireless LAN 2100 3B Mini PCI. I'm currently running Feisty Fawn.

When I go to systems>network this takes me to Network settings. In there I click on Wireless connection> properties, I unclick enable roaming mode and put in the wireless settings. I know it's working because under Network name (ESSID) it's picking up my network (which is password protected) and a few other ones that are not protected. I put WEP hexadecimal, but then I type the password in normally (it's 8 numbers long or something like that). Under configuration settings I've put automatic configuration.

When I go to network tools I get three network devices to choose from:
[LIST=1]
[*]Loopback interface (lo)
[*]Ethernet interface (eth0)
[*]Ethernet interface (eth0:avahi)
[/LIST]

Under loopback interface there seems to be some action going on, in that the interface statistics are showing packets transmitted and received, no collisions and no reception errors.

If I go to the ping tab and try and ping the router address which is 192.168.1.1 (or 192.168.0.1) I get nothing back.

I've checked the wireless information on the wiki but it's not specific enough. Any thoughts what I should do?

---

### Post by Unholy Moley on 2007-07-01
As the name implies, loopback loops back to your computer. Some programs utilize the loopback adapter for certain functions, which is why activity is evident. You should not be modifying the configuration of the loopback interface.

WEP is very weak encryption. It takes about ten minutes or less to crack. You should be using some form of WPA encryption. I have little doubt that your wireless card supports WPA, and if your router doesn't then either upgrading the firmware or replacing it is recommended.

I recommend against manually configuring the wireless card with the network settings manager and instead using NetworkManager in the tray (upper righthand corner). When you connect to a network with NetworkManager, you will be prompted for a WEP/WPA passphrase and it will store it for you. So enable roaming mode for the wireless connection in network settings and use NetworkManager.

---

### Post by khaledaboualfa on 2007-07-01
Aha, there seems to be a problem with my networkmanager. When I log on it comes up with an error:

**The NetworkManager applet could not find some required resources. It cannot continue. **

I uninstalled it and then downloaded it from the gb.archive.ubuntu.com/main/pool etc... and it's persisting to give me this message when I log in. Any thoughts?

---

