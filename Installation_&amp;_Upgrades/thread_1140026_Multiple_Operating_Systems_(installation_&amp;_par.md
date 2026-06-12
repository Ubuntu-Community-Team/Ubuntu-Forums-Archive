---
title: "Multiple Operating Systems (installation &amp; partition issues)"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Th3Professor on 2009-04-27
Okay, it was suggested elsewhere I split up a gob o' questions I had... here are some.

I have 5 hard drives:
1= OS (all boots and primary system files)
2,3,4= storage (raid5 & lvm)
5= external (movable storage)

OS:

[LIST=1]
[*] I've installed unix systems before just fine but for some reason it's not working now. How do I get sysV (Solaris), BSD (like OpenBSD), and other linux systems (like Gentoo) to work and also recognize hdd 2,3,4 (not for boot, just recognize and use after booting)?
[*]I have a "solaris boot" on a primary partition and a "solaris" (for all non-boot solaris files) on an extended partition. That should work, right?
[*]How do I include openbsd on the computer without having to sacrifice any of the current sda1, sda2, or sda3 boot options?
[/LIST]
 
Partitions:

sda1 = linux = /boot
sda2 = windows vista (with fuse, which isn't working right now, not sure why)
sda3 = solaris boot (not currently set-up)
sda5 = linux (system files only) = /
sda6 = linux (workspace) = /studio/workspace
sda7 = swap (striped priority with sda8 )
sda8 = swap (striped priority with sda7)
sda9 = solaris = not currently set-up
sda10 = linux (for secondary linux system, like gentoo) = not currently set-up
sdb1 = linux raid
sdc1 = linux raid
sdd1 = linux raid
sdi1 = vfat (fat32 default), external storage, used to read as sde1 (that's odd)


[LIST=1]
[*] Is there a more optimal arrangement and allotment of partitions and space for use with Ubuntu Studio, OpenBSD, Solaris, Gentoo, and Windows Vista?
[*]I'd like to see if I can include an OS on the external hard drive without losing and re-copying my current vfat/fat32 stored files. Is there a way to set-up the external hard drive to include a *nix OS without having to format the whole disk?
[/LIST]

---

### Post by Th3Professor on 2009-04-28
bump

---

### Post by Th3Professor on 2009-04-29
bump

---

### Post by Th3Professor on 2009-05-01
bump

---

### Post by dreza on 2009-05-01
Still learning alot of this myself (mostly trial and error at this point). But I do know windows is supposed to be at the begining of the drive in the first partition. That is most likely why windows wont work.
 
And unless I read it wrong, your having issues accessing the other HDD. The USB drive should mount on its own when plugged in, but the internal drives may not have a mount point assigned to them.
 
Someone with more experience can probably give you more definate answers.

---

### Post by Th3Professor on 2009-05-01
> **dreza said:**
> Still learning alot of this myself (mostly trial and error at this point). But I do know windows is supposed to be at the begining of the drive in the first partition. That is most likely why windows wont work.
 
And unless I read it wrong, your having issues accessing the other HDD. The USB drive should mount on its own when plugged in, but the internal drives may not have a mount point assigned to them.
 
Someone with more experience can probably give you more definate answers.

wow did you use your very 1st bean (post) on my thread? nifty. :)

anyway...

Windows is now working fine (via fuse) and has always worked fine as a normal boot.

The external hard drive (w/ usb) works fine. The internal hard drives work fine too - I am curious how to get them to work when using non-linux systems (aka sysv and bsd unix).

I suppose you could narrow my questions in the OP down to these 2:

How do I get the different Unix systems (non-linux) to actually work on this set-up?

How do I get them to recognize my raid5+lvm set-up on hdd2,3,4?

(OP has info on how the disks are set-up and their current partitions.)

---

### Post by Th3Professor on 2009-05-03
(*bump*)

How do I get the different Unix systems (non-linux) to actually work on this set-up?

How do I get them to recognize my raid5+lvm set-up on hdd2,3,4?

(OP has info on how the disks are set-up and their current partitions.)

(And all OS are going onto the separate 1st hdd.)

Thanks!

---

