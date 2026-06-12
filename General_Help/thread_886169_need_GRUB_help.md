---
title: "need GRUB help"
date: 2008-08-10
forum: General Help
---

### Post by BDubs588 on 2008-08-10
I am running a single Hard Drive system because I can't afford a new hd at the moment.  I had a windows partition and a Ubuntu partition.  I needed more space for Ubuntu so I used partition magic to resize the partitions to give Ubuntu more space.  In the middle of the process, I got an error about a floppy drive (I don't have one on my PC) and it aborted.  WHen I went to reboot, before the boot menu even came up, I got GRUB error 17.  I'm on an Apple right now because my PC doesn't have internet access which is the one I need to fix and I'd like to keep both partitions.  Please Help :confused:

---

### Post by confused57 on 2008-08-10
> **BDubs588 said:**
> I am running a single Hard Drive system because I can't afford a new hd at the moment.  I had a windows partition and a Ubuntu partition.  I needed more space for Ubuntu so I used partition magic to resize the partitions to give Ubuntu more space.  In the middle of the process, I got an error about a floppy drive (I don't have one on my PC) and it aborted.  WHen I went to reboot, before the boot menu even came up, I got GRUB error 17.  I'm on an Apple right now because my PC doesn't have internet access which is the one I need to fix and I'd like to keep both partitions.  Please Help :confused:
First I would recommend running a filesystem check on your Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

---

### Post by daveoily on 2008-08-10
i did something similar a while back, and I'll mention what I found, if it helps then great :)

grub it seems accesses a file on the linux partition to tell it where to boot from, using partition magic seems to kill grub off entirely.

I reinstalled ubuntu, ok so I killed off the previous install of ubuntu, but I got windows back, because grub was able to write itself back in there.

there may be a way of just installing grub, but I don't know it, when I'd finished doing that, I wished I had had a bit of a look around for that type of solution, depending on how much valuable data is on the ubuntu partition, you may want to look at that solution or just take the easy route :)

good luck!

---

### Post by sandysandy on 2008-08-10
have a look at this thread on how to install GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


other thread on how to install standalone GRUB

[http://ubuntuforums.org/showthread.php?t=880798](http://ubuntuforums.org/showthread.php?t=880798)

regards

---

