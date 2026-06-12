---
title: "No Sound - Alsa help - 7.10 server edition"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Forest_roby on 2007-10-24
HI!

At first sorry about my english!
I installed an ubuntu 7.10 server edition and I tried to make some sound but I couldn't.
I installed every alsa component but its not enough.

error messages:

alsamixer:
[I][SIZE="1"]forest@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
forest@ubuntu:~$[/SIZE][/I]

lspic:
[I][SIZE="1"]forest@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)[/SIZE][/I]

audio driver:
**00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)**

So... It is not working.

Can u guys help me to fix it?

thx!

Forest

---

### Post by TheSlayerIsBack on 2007-10-28
i have the same problem could someone please help us out

---

### Post by mempman on 2007-12-21
i also have this problem....anybody...?

---

### Post by DaveT on 2007-12-21
I believe this is the ALC883 chipset, its confuses me totally, its labelled as a Realtek, Intel and nVidia soundchip, i really dont know what to do with it now as the only help i found was about 18months out of date and none applicable to me :(

link is here
[http://ubuntuforums.org/showthread.php?t=202555&highlight=alc883&page=5](http://ubuntuforums.org/showthread.php?t=202555&highlight=alc883&page=5)

the problem with this thread is that its refereing to old versions of alsa which have long been replaced, but the problem continues.

I believe that the actual sound may be set up correctly it just doesnt output anything at all. this is rather annoying as i want to use my laptop as a MythTV front end, which it does wonderfully aslong as you like your TV muted :/

any help here would be appriciated, ive tried the Alsa website but their jargon makes me want to bury my head in the sand

---

