---
title: "No Internet on Atheros AR8132"
date: 2012-04-17
forum: Hardware
---

### Post by xbobby_bobx on 2012-04-17
Okay I know no one is gonna help me through this.. And I don't know why, I think I posted this over million times over the internet and nobody is willing to help.. Anyway I'm having a serious problem with the Ethernet interface on my laptop.. Once I try to download a big file or use the internet for a while.. The interface just stops and doesn't connect to anything.. Although it's saying that it's connected to the internet, and when I plug the wire off or reset the interface it try to connect to the internet but it won't and I have to restart the computer to get it working again.. Does anyone knows where I can find the official driver, or at least how to fix the problem?

P.S I'm running Ubuntu 11.10 with the latest updates.

---

### Post by Cyclane on 2012-04-18
Could we have the output of 'lspci -vv', I'd like to see the 'Ethernet controller' section.
There will be a section called 'Kernel modules' try to reload the modules with:
```
sudo modprobe -r MODULE
sudo modprobe -v MODULE
```

Reloading the module won't fix your problem but it might prevent you having to reboot the computer.

---

