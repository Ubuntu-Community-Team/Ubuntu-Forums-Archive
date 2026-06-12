---
title: "Can not install, reboots as soon as CD boots."
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by SkonOfVulcan on 2009-09-04
Please be kind I'm kind of new to Linux only done 4 installs so far. I searched the forums and can not find a solution to this. I'm beginning to suspect that it is a proprietary hardware problem.

The hardware: HP Touchsmart IQ505 (all in one with 22" touch screen),
   Intel Core2 Duo T5850 @ 2.16GHz, 4GB 800MHz DDR2, 500GB SATA (Hitachi)
   DVD+-RW (TSST Brand?),  Hard drive is partitioned 250GB for Vista Home Premium 64bit
   250GB free un-partitioned to be used by Ubuntu

What happens: I can boot to a live CD and play around with Ubuntu 9.04 32bit & 64bit (same thing several months ago with 8.xx), however if I try to boot and install as soon as I choose to install the system reboots! I know the CD is good as I checked it with the included utility and also used it to install on three other systems with no problems since then. Have tried a different CD with same results. Also when I tried installing Ubuntu 8.xx a few months ago I got the same response. There are never any error messages.

I'm beginning to suspect that it has something to do with the hardware. i.e. the DVD/CD drive which is a slot loading, laptop, low profile type. Or possably because HP tie's the OS to either the hard drive or motherboard via a firmware copy of the Vista Product Key. Or some such nonsense. I've seen it before with some Dell systems. (It figures. This is the first time I DIDN'T build my own system & bought one pre-built. Won't happen again.)

So if anyone has come across this problem before and knows the answer or has any ideas or suggestions I'd appreciate any input you have!

Regards,

Skon

---

### Post by imhotep59 on 2009-09-04
Hello,

Maybe you can try to install with a USB key. I think you can create a bootable USB key with the liveCD. I am not sure because i am not in front of may desktop but i think it is in the system menu administration. A 1 Go key is needed.

---

### Post by Yvan300 on 2009-09-04
Have you tried jaunty jackalope. It may be an installation bug that has been fixed in the newer version. Also you could try other distros so as to test weather it is your drive or just that particular version of ubuntu. 

Good luck

---

### Post by ronparent on 2009-09-04
SconOfVulcan: Try booting to the live cd (you have said that works) and click on the install icon on the desktop once booted. Maybe this will by-pass whatever glitch you are having from the install menu? Let us know your progress.

---

### Post by presence1960 on 2009-09-04
Instead of trying to launch the installer from the menu at CD boot, choose "try Ubuntu without any changes". When the desktop loads try the install icon on the desktop.

You can try making a bootable USB with [unetbootin]("http://unetbootin.sourceforge.net/"). if you have another machine with Ubuntu 9.04 under System > Administration > USB Startup Disk Creator will also do the job.

---

### Post by SkonOfVulcan on 2009-09-07
> **ronparent said:**
> SconOfVulcan: Try booting to the live cd (you have said that works) and click on the install icon on the desktop once booted. Maybe this will by-pass whatever glitch you are having from the install menu? Let us know your progress.

Finally got the chance to try out your (and a couple of other peoples) suggestion last night. Success! That did it. Installed with no problems after booting to the live CD desktop and installing from there.Thanks!

Now the question is 'why' will it install one way but not the other. I would like to know. The more you know about this kind of thing the better prepared you are when there is a problem.

Now on to better stuff!:popcorn:

---

