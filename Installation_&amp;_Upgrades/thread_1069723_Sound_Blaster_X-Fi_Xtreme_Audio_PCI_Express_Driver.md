---
title: "Sound Blaster X-Fi Xtreme Audio PCI Express Driver"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by stevot on 2009-02-14
Hi all,

An install of Kubuntu 8.10 on the desktop is working great, with the exception of sound:

steve@kubuntu-master:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
steve@kubuntu-master:~$ lspci -v

---snp

03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
        Subsystem: Creative Labs Device 0018                         
        Flags: bus master, medium devsel, latency 32, IRQ 12         
        Memory at d2000000 (32-bit, non-prefetchable) [size=16K]     
        Capabilities: <access denied>                                
 ---snp


This is a pain since Ubuntu is much better for work than the other OS on it (XP) but I need music whilst working.

Reading around it sounds like this card is actually an Audigy one with  emu10k1 chipset rather than a true X-Fi. In which case I should be able to get it working. Can anyone help me out with this? Am I right in this interpretation, and if so can you point me to a driver that they know works ?

Thanks for any help,

Stevo

---

### Post by smani on 2009-02-24
Hello,
drivers for the ca0110-ibg are in developement, mandriva already includes an experimental version in one of their kernels, see for example [http://rpmfind.net/linux/RPM/mandriva/2009.0/i586/media/contrib/testing/kernel-tmb-desktop586-devel-2.6.27.15-2mdv-1-1mdv2009.0.i586.html](http://rpmfind.net/linux/RPM/mandriva/2009.0/i586/media/contrib/testing/kernel-tmb-desktop586-devel-2.6.27.15-2mdv-1-1mdv2009.0.i586.html) or google for it. I can remember reading somewhere that the driver is also included in the unstable alsa driver, can be downloaded from git somewhere, I cannot find the link right now, but you should be able to find it in google also. I hope it will manage to get into mainstream ALSA this year, maybe 1.0.20? Patience...

smani

---

