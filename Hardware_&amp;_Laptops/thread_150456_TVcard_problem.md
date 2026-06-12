---
title: "TVcard problem"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by Vinger on 2006-03-26
Hello,

I bought a secoundhand tvcard. (pinnacle studio PCTV rave)
Last week, i installed the card and she was autodetected (like i had read in [http://ubuntuforums.org/showthread.php?t=126292](http://ubuntuforums.org/showthread.php?t=126292))

This weekend, i tried to watch tv again on my pc, but the card isn't recognized anymore...
TVTime give the error > cannot open capture devic /etc/video0
I tried the command lspci
> 
koen@Kubuntu:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP 

This week, there is nothing changed on the computer. (he has only been started in Windows once! The drivers for windows are not installed yet...)

What can be the problem?

tx, grz

---

