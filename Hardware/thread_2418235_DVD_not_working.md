---
title: "DVD not working"
date: 2019-05-03
forum: Hardware
---

### Post by Jockboy98295 on 2019-05-03
Never had this problem before, but could be my computer. I've done a search and created the mount point, but still doesn't do anything. From a terminal "eject" does operate the dvd drive and "ls /dev " does list the drive. Inserting and disk does nothing but make the drive light flash. Terminal always says "no medium found on /dev/sr0". Any ideas? 

Computer: Dell Optiplex 9010
Output of "sudo lshw -C drive";

description: DVD-RAM writer
       product: DVD+-RW TS-H653G
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: DW10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc


When a disk is in the drive and the light is flashing status will change to busy, then to no disk. 
Any help is appreciated.

---

### Post by CatKiller on 2019-05-03
Lenses sometimes get dirty, or fogged up. Lens cleaning discs are cheap.

Disks sometimes get scratched, meaning that the part that identifies them as there can't be read.

Lasers sometimes become mis-aligned or fail. DVD drives are pretty cheap.

---

### Post by Jockboy98295 on 2019-05-12
While all of that may be true, it boots off a cd or dvd no problem. Its not broken. Why is ubuntu not reading the drive as a dvd? it works great in ubuntu as a cd. Even windows reads it and it works great, and thats through VirtualBox.

---

### Post by CatKiller on 2019-05-12
> **Jockboy98295 said:**
> While all of that may be true, it boots off a cd or dvd no problem. Its not broken. Why is ubuntu not reading the drive as a dvd? it works great in ubuntu as a cd. Even windows reads it and it works great, and thats through VirtualBox.

Your initial post appeared to be saying that the drive wasn't recognising discs.

> When a disk is in the drive and the light is flashing status will change to busy, then to no disk. 

No mention that it was reading some discs but not others.

If the issue is that you can't play **video** dvds, you need to install something that's able to decrypt them: ubuntu-restricted-extras or libdvd, I think, although I don't have an optical drive myself to check.

If the issue is something else, you're going to need to be a lot more specific before anyone can help you.

---

### Post by Jockboy98295 on 2019-05-19
What info do you need? Restricted is already installed.
Thank you.

---

### Post by Jockboy98295 on 2019-05-19
Sorry if I seem snappy or whatnot. I work night shift and am an endlessly tired zombie.

---

### Post by CatKiller on 2019-05-19
> **Jockboy98295 said:**
> What info do you need?

A clear description of the actual problem.

---

