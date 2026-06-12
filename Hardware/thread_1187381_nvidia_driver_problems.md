---
title: "nvidia driver problems"
date: 2009-06-14
forum: Hardware
---

### Post by spursncowboys on 2009-06-14
I just installed ubuntu9.04 amd 64 and went to system-admin-hardware drivers. then I selected the 180 version (recommended). I reboot. Did it all over again and rebooted again. My screen was black. So I went to safe mode and did the auto fix option (it was the tab at the bottom).

---

### Post by 67GTA on 2009-06-14
You need to run ```
sudo nvidia-xconfig
``` to set up your xorg.conf file. Also if you have a TV tuner card that uses the cx18 driver, it will conflict with the nvidia driver at boot. [http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)

---

### Post by spursncowboys on 2009-06-14
> **67GTA said:**
> You need to run ```
sudo nvidia-xconfig
``` to set up your xorg.conf file. Also if you have a TV tuner card that uses the cx18 driver, it will conflict with the nvidia driver at boot. [http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)
I reboot, then my computer got froze on 'gateway f2 f10' screen. I turned off/on my comp. and then hit f10 and when I booted the hd, it was an all blank screen. I went to safe mode and xfix'd it.

EDIT: I ran lsmod | grep cx18 and got nothing.

---

### Post by spursncowboys on 2009-06-16
:popcorn:

---

### Post by PetterDK on 2009-06-16
Try using EnvyNG to remove the nvidia drivers, then installing the new driver by first dropping to ctrl+alt+F1, stopping gdm, sh the driver and then reboot..

It should be said though that the newest driver did not work for me. I had to go to the driver archives at nvidia.com and find an older driver. As I recall, it was the 180.29 driver that had a problem, so I had to install 180.17 which worked perfectly..

EDIT:
to install EnvyNG:
Gnome: sudo apt-get install envyng-gtk
KDE: sudo apt-get install envyng-qt

---

### Post by spursncowboys on 2009-06-16
I installed EnvyNG. Then I could not find a GUI. So I, following the directions from [http://ubuntuforums.org/showthread.php?t=1125400&highlight=uninstall+drivers](http://ubuntuforums.org/showthread.php?t=1125400&highlight=uninstall+drivers) I did it and got my screen resolution to work. However I still cannot get 3D graphical effects. 
This is my lspci 
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

```

---

### Post by spursncowboys on 2009-06-19
Thank you everybody for all the help. I installed EnvyNG, 
```
sudo apt-get install envyng
```
then I ran envyng through text```
envyng -t
```
then I uninstalled my driver. Now I am installing my 180.60 driver. Thanks again.

---

