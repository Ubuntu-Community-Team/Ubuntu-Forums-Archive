---
title: "No internet connectivity from apps"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by mnasimh on 2009-02-10
Last night I have updated my 8.10 box from kernel 2.6.27-9 to 2.6.27-11. After the update, no applications from Ubuntu can connect to internet. Network Manager has the connection to my eth0 LAN card. I can ping to anywhere implying my computer is connected to the internet. But not a single appliction including Firefox, Konqueror, Opera, Kopete, Pidgin, XChat can connect to the internet.

However, I have a VirtualBox instance of Windows XP running with Host Interface. From this guest Windows XP I can connect to the internet. In fact, I am writing from it now. But if I change the VirtualBox network adapter from Host Interface to NAT, I cannot connect to the internet.

This is really strange. My connection is alive, but no program can access it except guest OS in VirtualBox with Host Interface (not NAT).

I have tried to restart the networking. Even computer reboot. I have also disabled firewall with the help of FireStarter. Nothing works. Can somebody point me somewhere, please?

I have also tried booting into the previous kernel. But with no luck.

---

### Post by mnasimh on 2009-02-10
I have found the problem. My eth0 was loading in promiscus mode. I have to disable it running:
```
sudo ifconfig eth0 -promisc
```

I guess VirtualBox is causing this problem. It is creating a bridge pan0 to use Host Interface networking which forces eth0 into promiscous mode. I am not sure if I have to disable this mode again if I reboot my machine.

---

