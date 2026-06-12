---
title: "Accidental MBR erase, now need to restore it"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by linkxs on 2009-09-19
Hi there,

I had win 7 + ubuntu 9.04 and I accidentally erased mbr, forgetting that it'd kind of kill the partition table. how would i restore it? I really need to have it back up by midnight (5 hours). 

There are about 8 or 9 partitions there. 

Thanks for any help.

---

### Post by dreamingdarkness on 2009-09-19
It depends which MBR you want to reinstall - If your most urgent need is a working system, you need one of two things: an Ubuntu Live disk or a disk with Windows 7 on it.
With a Linux LiveCD you should be able to either pull GRUB up and fix the MBR or fix the MBR manually (much more advanced, I can't guide on that!).

If you have or can burn one, a Super Grub Disk from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) will let you re-write GRUB into the MBR and should re-write the MBR. You could re-write a Windows MBR but it won't let you access your Linux partition then.

With Super Grub disk, try to autofix or boot without the MBR being recovered, then if you have a backup you can restore from it or at least get what you need done. Not sure if this helps, but I hope it does!

Instructions that might help are here:
[http://members.iinet.net/~herman546/p18.html](http://members.iinet.net/~herman546/p18.html)

---

### Post by linkxs on 2009-09-19
thanks for the reply,

I only marked this thread as solved because i moved it here:

[http://ubuntuforums.org/showthread.php?p=7977292&posted=1#post7977292](http://ubuntuforums.org/showthread.php?p=7977292&posted=1#post7977292)

i was thinking of trying the supergrubdisc, i'm gonna try it now

---

### Post by dreamingdarkness on 2009-09-19
Ah, it got marked resolved between my opening it and replying. Glad to see you're getting help on it! Good luck, and SuperGrubDisk has saved my bacon a number of times, hope it does well for you. That or TestDisk as someone else mentioned.

---

### Post by linkxs on 2009-09-19
just tried super grub disc, didn't work. tomorrow when i get the sata external enclosure i'll try testdisk.

---

