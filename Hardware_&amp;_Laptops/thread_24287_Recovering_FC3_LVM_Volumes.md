---
title: "Recovering FC3 LVM Volumes?"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by cdiorio on 2005-04-06
Hi all, I hope someone can help me out, or at least point me in the right direction.

I had an lvm volume group in FC3 with two hard drives in it. One of the disks developed a bad superblock (at least that's what I'm led to believe by the diagnostics I have run). I had been thinking about making the change to Ubuntu, and thought this would be as good a time as any. I thought it would be no problem to at least mount the good one under Ubuntu and recover the data. Soooo.....

I bought a new big fat 160 GB drive and installed Ubuntu - it's up and running (a few tweaks, etc., required,  but I'll leave all that for later). In the past, I've done something similar to this, and not had a problem, but that was without LVM. Since I'm basically unfamiliar with LVM, I'm at a bit of a loss.

At present, I've made images using dd of the drives. I've fiddled around with them using some of the LVM tools (and I hope I haven't made it worse.). I'm now reconciled to the fact that I probably can't figure this one out on my own...

Does anyone out there know what approach I should be taking? I just need some of the files - I'm not concerned with resurrecting the filesystem or anything like that.

---

### Post by ryness on 2005-04-23
did you ever find a solution to your problem? i put an existing fc3 lvm raid5 into a box with ubuntu on it and i get: 

root@server:/livebak # fdisk -l
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       77799   624816045   8e  Linux LVM

root@server:/livebak # pvscan
  PV /dev/sda2   VG VolGroup00   lvm2 [595.84 GB / 32.00 MB free]
  Total: 1 [595.84 GB] / in use: 1 [595.84 GB] / in no VG: 0 [0   ]

root@server:/livebak # lvs
  No volume groups found


??

---

### Post by cdiorio on 2005-04-24
Nope, haven't managed to fix this one at all. In fact, I'd pretty much given up on even checking here to see if there was an answer. 

My problem is that I'm really a complete newbie when it comes to the LVM stuff, and have no real understanding as to what it is that I'm doing...

Let me know if you get anywhere with yours. I've tried a bunch of things (e2salvage, etc., stuff like that), but I don't know enough about how LVM works to know how to deal with it.

---

### Post by mike55 on 2005-05-20
Hi guys, not sure if this is still an issue for you, but I was curious about it myself. I was running FC3 and used the instructions in the LVM Howto at [http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)
to view my FC3 lvm volumes from the Ubuntu live cd.

Mike

---

