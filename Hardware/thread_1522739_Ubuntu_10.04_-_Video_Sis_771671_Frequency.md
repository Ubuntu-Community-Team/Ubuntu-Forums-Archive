---
title: "Ubuntu 10.04 - Video Sis 771/671 Frequency"
date: 2010-07-02
forum: Hardware
---

### Post by rata71 on 2010-07-02
Hello, i have a notebook Packard bell EasyNote MH35 with a video SIS 771/671.
I've already set the video to see the desktop in a resolution of 1280x800, but when the Ubuntu boot(starts, after grub) the screen is losing sync.
My big problem is that when you start, it shows the screen as if he had lost the sync and if you see any messages, such as "Checking disk ..." I did not hear about what appears on the screen. And when it finishes booting, I see my desktop perfectly, but I can not access the consoles


root@sys-01:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04 LTS
Release:        10.04
Codename:       lucid


root@sys-01:/# lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

root@sys-01:/# cat /etc/X11/xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "sis671"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


tks
Gabriel

---

### Post by mhgsys on 2010-07-25
read;

[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)


;)


You'll find how to fix tty and plymouth.

---

### Post by mhgsys on 2010-07-25
double posted.. 

sorry

---

