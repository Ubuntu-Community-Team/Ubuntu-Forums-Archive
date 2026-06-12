---
title: "T22 Won't boot up after fresh install..."
date: 2005-11-10
forum: General Help
---

### Post by acascianelli on 2005-11-10
I just got a IBM T22, 900mhz P3, 256mb ram, 40gb hdd.  I installed Ubuntu Breezy on it just fine, everything went great, no problems at all.  After it finished the install on the CD, it rebooted and continued the install till I got to a desktop.  I did some updates, and went to reboot and it will not boot up anymore.

It won't even boot up off the Ubuntu install cd anymore.  I also tried a Gentoo Live CD and it will not boot off that either.

I tried a Knoppix 4.0.2 CD, and it finally did boot to a desktop, but I'm clueless as to why it will not boot to the installed Ubuntu system anymore.  I'm hoping somebody can give me some answers.

---

### Post by acascianelli on 2005-11-13
I removed the mini-pci Intel 10/100 network card and that seems to have fixed it for now...

I'm going to see if it was the network card or the mini-pci slot that is bad.  Hopefully the network card.

---

### Post by tedrogers on 2006-08-07
I have tried reoving PCMCIA cards and it makes no difference for me as my T22 wont go any further than the "mounting root filesystem" section of the live DVD bootup. The drive just gurgles and makes lost of noises that sound very bad!

I have had no other problems with the drive though. It works for everything else I have installed, and many other linux live DVD/CD distos including Slax, Gentoo, Suse, DSL and Knoppix.

The T22 has the Savage gfx chipset and I've heard this can cause problems....but basically I'm stumped.

Also I can't get kubuntu installed either.

Any ideas what's going on?

Thanks.

---

### Post by The Road Below on 2006-08-11
Try xubuntu.  Had similar experience with ubuntu and t22.  xubuntu worked for me.

---

### Post by tedrogers on 2006-08-17
Thanks for your reply.

Yes...I've tried that too and the Xubuntu Live DVD reacted exactly the same as the Ubuntu Live DVD.

However...other distro's like the DSL and Knoppix Live CD's work excelently.

Stumped!?


-----------------------------------------------------------------

This is all sorted now, through installing through text mode and using fiddling with the xconf. You can read how I fixed my problem here:

[http://www.ubuntuforums.org/showthread.php?t=214153&page=2&highlight=t22](http://www.ubuntuforums.org/showthread.php?t=214153&page=2&highlight=t22)

---

