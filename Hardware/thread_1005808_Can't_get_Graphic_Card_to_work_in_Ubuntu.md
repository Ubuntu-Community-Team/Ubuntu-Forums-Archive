---
title: "Can't get Graphic Card to work in Ubuntu"
date: 2008-12-08
forum: Hardware
---

### Post by joe2me on 2008-12-08
I'm stuck on 800*600 in resolution at most:/ 

Have a Nvidia Geforce 7300 GS inside my computer but can't get it working. Tried enabling the hardware driver. Tried installing using synaptic pack manager. Tried using EnvyNG.

How to get it working and get a higher resolution?! 
And what more info do you need from me to help me?!

---

### Post by damis648 on 2008-12-08
Is the resricted driver active? If it is, run in terminal
```
sudo apt-get install nvidia-settings
```
and that will install nVidia's settings utility. Now type
```
gksudo nvidia-settings
```
and see if you can change the resolution.

---

### Post by joe2me on 2008-12-08
It seems like the restricted driver is not active and when I try and activate it and re-start I got the following error message->

"Your screen and graphics card could not be detected properly..."

 I tried putting them in manually but it still didn't activate the restricted driver. 
My screen is a Hansol 900p if that helps...

---

### Post by joe2me on 2008-12-09
Found the problem... It uses the built in graphic card (MCP55) that my motherboard has instead of my Geforce one.   How do I make it use the right one? And how to uninstall the drivers I already installed?

> joe2me@ice:~$ lspci | grep -i nvidia
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
06:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)


---

### Post by linux_tech on 2008-12-09
I would first see if there is option in bios to disable onboard video. 
These may help to get your video card going
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by joe2me on 2008-12-09
I uninstalled anything that had to do with the drivers and then used EnvyNG to install them again which somehow fixed the problem this time:D

Thx for your help! PROBLEM SOLVED!

---

