---
title: "SBx00 Azalia ?? Forcing Brutely Shutdown of whole computer"
date: 2008-09-12
forum: Hardware
---

### Post by dpgraves on 2008-09-12
Running Ubuntu 8.04 32bit on a Gigabyte GA-MA74GM-S2H
running a older AMD chip AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
2x1 gig Kingston Ram 800mhz DDR2
Nvidia GeForce 7300 GS with 512Mb PCI-E 16x
Brand new 240Gb Sata Drive

dpgraves@wurn-amd:~$ uname -a
Linux wurn-amd 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

dpgraves@wurn-amd:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7911
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

What i Get are hard reset x stops. ssh connections fail and only way out is holding in the power button.
DVD drive fasts activity then system shutsdown

only happens when playing sound of some kind either via firefox websites eg myspace. or any other website that plays music via stream

or by amarok will do it as well.

haven't had it playing movies avi's

sound device both alsa and alc883 analog

tried removed both ide cdrom and dvd drive to take them out of the problem still crashes.(tried disabling via bios but it still active in ubuntu but not on bootup same with sata drives )

have disabled the sound device in bios same problem just took longer to crash (not sure if actually disabling fully but sound device is no longer present.)

can provide any other logs if required just want to know how to stop the crashes.

Also did further testing overnight 

Further testing frequently happens with firefox3.0 when it produces sound. youtube fine by itself.
myspace by itself will take a while to or few random page changes before it crashes.

but if you are running both it will crash straight away.

Also Playing DVD's it crashes after 5min or so.
can play avi all day no problems.

Please let me know what other info would make this easier to find the cause.

Ran AVI fine ran amarok with over 4hrs of music fine (running by itself)

Also posted on launchpad just need an answer or find out what my next step is. 

Tested on Intreped Alpha 5 live will not even boot same style lockup out trying to load the live gnome

Let me know what logs or any other info that would help fix this.

---

### Post by cariboo on 2008-09-12
I would suggest you run memtest to check your ram. Builtin peripherals share ram and its acting like a ram problem.

Jim

---

### Post by dpgraves on 2008-09-13
Have run Memtest built in to Ubuntu also run memtesters from ubcd all  come up clear.

Also swapped memory with some older ddr2 so only tried 1 gig 2x512mb.

tried each slot individually with different modules same issue.

so not physical memory ( may be overlap of memory. but not sure where to look)

unless producing some kind of sound other than from avi it will crash no sound will sit there all night no problems.

---

### Post by dpgraves on 2008-09-15
Looks like getting kernel panics set panic=5 on boot and was a lot more stable and can get onto myspace now for around 5min with no crashes then it actually restarts not halts.

should this be marked as a bug now if so what logs are required to set as bug.

setting in menu.lst to panic=15 to try and make more stable.

is there any other options i need to add to be able to track the panics first look I cannot see anything wrong but not sure what to look for.

Please help Damien

---

