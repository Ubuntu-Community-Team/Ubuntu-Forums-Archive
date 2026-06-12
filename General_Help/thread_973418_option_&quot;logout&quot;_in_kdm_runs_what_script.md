---
title: "option &quot;logout&quot; in kdm runs what script"
date: 2008-11-06
forum: General Help
---

### Post by maestrobwh1 on 2008-11-06
Acer Aspire LCi 3000 Laptop.  I have one issue with Intrepid... everything works except something kind of annoying:  I can't log out.  Shutdown, Restart, Suspend, Hibernate all work properly.  When Shutdown or Restart are chosen, I do see a short notice before usplash starts that kdm is stopped.  However, logout produces the following thing

** checking battery state


And there is no prompt.  I have to 

ctrl-alt-F1 to get a console login where I can issue

sudo /etc/init.d/kdm restart

There was a timidity message after that, so thinking it was that package, I removed it.  It has nothing to do with the battery or anything causing the hang I think... The logout option is simply not running.  

/etc/init.d/kdm restart

It is possible I suppose that it can't restart, but I see no error messages, and using ctrl-alt-F1 stops it... and it stops during shutdown/reboot.

So if I knew which script file runs when I select "logout" from my menu, that would be grand.

I tried using another login manager, **xdm and gdm and I get the same problem...** so it isn't the login manager, but a failure of kde to not run the appropriate script.  The login manager works from a fresh start/reboot.

My hardware:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

