---
title: "NVidia 6100S"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by kiplingku on 2006-12-11
Hi, I'm going to use Ubuntu that I just got on my computer, I'm using ECS GeForce6100SM-M mobo with following specs:
Integrated Graphic NVidia 6100
Onboard Broadcom AC131 NIC
Onboard Realtek ALC660 SoundCard
and NVidia IDE Controller..
Since I'm new to Ubuntu as well as Linux, does anyone know how to install the above hardware? And which Ubuntu I need to use? Is it the 386 or 64 version? I managed to install the 386 version, but its so slow.. (I'm using Athlon 64)..
Kindly anybody help me on this.. I really like Ubuntu.. And I couldnt afford Windows XP..
Thanks..

---

### Post by jonpackard on 2007-03-23
Hi kiplingku. I would recommend starting with the 386 live CD. You are not likely to notice a significant performance boost by switching to 64-bit. The 64-bit Ubuntu is great but I find it can be a challenge to set up and use, depending on what you need it for. You might also be interested in [Linux Mint]("http://www.linuxmint.com") (an Ubuntu based distribution). I just built a computer using the same motherboard you have. I have booted several Ubuntu-derived distributions on it and I have experienced two problems so far. The integrated network interface and integrated sound device are not recognized properly. I am still playing around with them. I will post again when I have made progress. Here is a listing of my PCI devices:

ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d1 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

---

### Post by 1tiger1 on 2007-04-09
Same problems here. I have tried with Edgy and am trying gain tomorrow with Feisty. This will be my fifth ubuntu installation, and so far, my first actual problem :( 

I'll post any progress I make with Feisty, but I am not holding my breath for too long. This thread here:

[http://ubuntuforums.org/showthread.php?t=379756]("http://ubuntuforums.org/showthread.php?t=379756")

seemd to indicate that this is a problem that will only be solved with the .20 kernel AND some magic probing.

---

### Post by 1tiger1 on 2007-04-09
Okay, I downloaded Feisty beta, installed, and I am posting this on my browser, using my on board network card while listening to my sound card. 

And wow, this board and processor (AMD Athlon 64 X2 4600+) SCREAMS!

---

