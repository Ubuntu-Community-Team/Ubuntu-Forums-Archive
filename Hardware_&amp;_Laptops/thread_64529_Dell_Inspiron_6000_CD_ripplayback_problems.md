---
title: "Dell Inspiron 6000 CD rip/playback problems"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by hielscher on 2005-09-11
Hi,

I've had Kubuntu Hoary installed on my Dell Inspiron 6000 laptop for a few months, and until now I haven't cared about the sound and video playback not working properly as I had access to other methods for doing those things, but I've since moved to Europe from the US and now my laptop is my sole means of electronic enjoyment.

I've been trying numerous things to get my sound to work properly to no avail.  The problems are as follows.  When I play an audio CD in the drive with something like kaffeine or the CD player the player can freeze up.  I'll have to kill the process and then the CD drive gets locked up -- restarting KDE doesn't help, and I end up rebooting.  After this no audio programs can be started, they all fail upon startup.

In addition, CD ripping doesn't work properly.  I haven't been able to get my CD drive DMA enabled, so ripping is very slow.  Also, no matter what I use to rip (KDE's automagic ogg through Konqueror, KAudioCreator, Grip, Sound Juicer) after usually one but sometimes two or three songs of ripping, I get the same lock up problem.  When I use cdparanoia I get full system lockups which require a reboot, while with cdda2wav I just get the above mentioned drive lockups.

I've tried recompiling my kernel with the Allow DMA for non-hard drives option, with the ata_piix and libata.h files edited as described in this thread [http://ubuntuforums.org/showthread.php?t=35738&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=35738&page=2&pp=10), I've tried adding piix and ide-core modules above the other modules in my modules file and some combinations of the above to try to get DMA working.  Nothing has helped me get DMA enabled or solved my audio freezing problems.

Any ideas?  It seems like this is a common enough problem that there should be a pretty exact solution.

Thanks.

---

### Post by mlord on 2005-09-11
[QUOTE=hielscher]
I've tried recompiling my kernel with the Allow DMA for non-hard drives option, with the ata_piix and libata.h files edited as described in this thread [http://ubuntuforums.org/showthread.php?t=35738&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=35738&page=2&pp=10), I've tried adding piix and ide-core modules above the other modules in my modules file and some combinations of the above to try to get DMA working.  Nothing has helped me get DMA enabled or solved my audio freezing problems.[/QUOTE]

The kernel rebuild with "#define ATA_ENABLE_ATAPI"  *always* fixes the DMA issue.  If it didn't fix it on your system, then you've left out a step or done something wrong somewhere.

cheers

---

