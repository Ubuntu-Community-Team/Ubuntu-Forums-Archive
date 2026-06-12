---
title: "USB Now Working With Averatec 3200"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by jacksonyee on 2005-05-12
Greetings!

I had been having issues with USB not working anymore after hotplug, whether it would be an optical USB mouse not having any light, an USB flash drive, or an USB hard drive.  This is on an Averatec 3200 notebook computer which Knoppix and Gentoo hotplugged USB just fine, so I knew that it was possible for USB to work on this computer.  After running through several kernel configurations, USB is now working by compiling usbcore and the host controllers ehci, uchi, and ochi directly into the kernel instead of compiling them as modules.  All USB devices that I've tried work perfectly now.  Just thought I'd offer this suggestion to all of the people having troubles with hotplug and USB.

Now, if I could only get the DRI for my Unichrome AGP and my VIA Rhine LAN not to conflict, I'd have everything working...

---

### Post by fluideye on 2005-05-12
So you have sound?  I have an Averatec 3200 as well and can't get my sound right.  I had it working last night by unmuting in alsamixer but can't get it going today.  Any tips?

---

### Post by jacksonyee on 2005-05-12
I had sound from the very first install and haven't had any issues with it.  alsamixergui is a good way of managing the sound, although gnome-mixer works quite well.  

The module is actually called snd_via82xx, which you can check by typing "lsmod | grep via"  There's a thread at [http://ubuntuforums.org/archive/index.php/t-1994.html](http://ubuntuforums.org/archive/index.php/t-1994.html) which discusses some parameters to set in /etc/modprobe.d, specfically adding "options dxs_support=4" to /etc/modprobe.d/alsa-base

Let me know if you have any further troubles with it

---

### Post by fluideye on 2005-05-12
Lucky you!  I actually just found a thread that fixed my problem (I hope, I've rebooted several times and shut down several times so hopefully so).

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

Are you having problems with while booting up with

configuring network devices
cs: pcmcia_socket0: unable to apply power  (this is where the loop begins for about 50 lines)

Thanks for your help!

BTW: love Averatec and Ubuntu!

---

### Post by jacksonyee on 2005-05-12
I just tested my notebook with my PCMCIA firewire adapter - it didn't have any issues.

Apparently, this message happens with many other computers:

[http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html)

 The strange part is that even computers with the exact same configuration can sometimes get this message and sometimes didn't.  Hopefully the kernel team can resolve it.  You could always try compiling a new kernel or upgrade to a new version and see if it resolves your issue.  Just make sure that you add "noinotify" to your kernel boot parameters if you use a 2.6.11 kernel.  I'm staying on 2.6.10 right now because of issues with hotplug and DRI that I've found with 2.6.11.

---

### Post by fluideye on 2005-05-13
Yeah, from the feedback I want to stay away from 2.6.11 too.  Haven't heard great things yet about that version.  I put in a bug report so hopefully I can get some help there.

---

