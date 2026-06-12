---
title: "MSI GP62 2QE Leopard Pro - Unable to install any Ubuntu/Linux distribution at all"
date: 2016-02-16
forum: Hardware
---

### Post by Pedro_Lopez on 2016-02-16
Hi Guys,

The specs for this laptop are ( the ones that I think that matter ):
5th Generation Intel® Core™ i7 Processor ( Intel I7 5700 HQ )
NVIDIA GeForce GTX 950M 2GB DDR3 VRAM


I recently bought this new computer and I'm struggling very hard to install any Ubuntu/Linux on it. So far, this is what I've tried without success:


- Even though I'm not a big fan of them, I've tried to use virtual machine software: Virtual Box and VMWare. I've used several distributions on them ( Ubuntu 15.10, 14.04 LTS, 14.10, 15.04, etc.. 64 bits ) and I always end obtaining the famous blue screen ( you know, the blue windows "death screen" ).  

Checking the forums, I found that perhaps it was an issue related with the BIOS so I modified the BIOS to enable the Virtualization options: nothing changed. If it's useful, I'm running these apps in Windows 10 ( not original :P ).

- Tried installing Ubuntu 14.04 LTS, 14.10, 15.04, 15.10, Linux Mint 17 ( cinnamon ), Linux Mint 17 ( KDE ) in native mode. Results from them were that only Ubuntu 14.10 goes though the loading screen and I'm able to install it. Unfortunately this version crashes randomly whenever I'm working with it.

Checking some threads from this forum, I found and tried this one that looks really similar to my problem but it didn't helped me: [http://ubuntuforums.org/showthread.php?t=2284315](http://ubuntuforums.org/showthread.php?t=2284315)

Being said all this, I'd like your help as I really need the computer for college and I'm using the old laptop that I had when I bought this one. If you feel, that it would be easier to make ubuntu works in virtual machine, please go ahead and focus on that part. If not, please help me to make ubuntu work in native mode.

Please, if you need any other information just let know and I'll try to provide all of it.

Thanks in advance for your responses,
Pedro

---

### Post by oldfred on 2016-02-16
I do not know about virtual installs, and what changes that may require.

But other with MSI laptops have needed various boot parameters. Not sure if different ones work, or models are enough different that the same parameter only works on some models.
The nomodeset is required if booting with nVidia, but if booting with Intel video then a Intel parameter is required.

Only use current releases and new systems need newer versions of Ubuntu. Current versions are 14.04LTS and 15.04. The 14.04.4 version will be out in a couple of days on the 18th. If willing to experiment 16.04 will be out in April, but daily update version is available now, but may break as things are updated.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

