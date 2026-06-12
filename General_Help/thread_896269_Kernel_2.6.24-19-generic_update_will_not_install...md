---
title: "Kernel 2.6.24-19-generic update will not install..."
date: 2008-08-21
forum: General Help
---

### Post by diablo75 on 2008-08-21
I have one update pending inside my update manager.  It is the linux-image-2.6.24-19-generic update.  It fails to install, and produces the following error message:

> E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_amd64.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

This is an 8.04.1 Wubi install which is sitting on a FAT32 partition, if that matters.  Thanks in advanced!

---

### Post by prshah on 2008-08-21
> **diablo75 said:**
> 
produces the following error message:


Have you run out of disk space by any chance?```
df -h && df -hi
``` will tell you.

---

### Post by diablo75 on 2008-08-21
Certainly not.  The space allocated to the Wubi install was 30 gigs and very little has been done with it since installing.

I'm not going to put much of a priority on this update right now, as we're about to wipe the hard drive it sits on clean ext3 partition.  If this same isolated update problem happens still, I'll check back here.

---

### Post by prshah on 2008-08-21
> **diablo75 said:**
> 
This is an 8.04.1 Wubi install which is sitting on a FAT32 partition, if that matters.

> **diablo75 said:**
>  space allocated to the Wubi install was 30 gigs 


Whoopsy; FAT32 cannot handle files larger than 4Gb (3.9 GiB for nit-pickers) so it's unlikely that your 30Gb (virtual) disk/partition has been successfully created with the full capacity.

Wubi creates a "file" that acts as a "loopback drive device" which is shown to Ubuntu as a drive/partition, and Ubuntu works off that. Since FAT32 cannot create single files larger than 4Gb, I believe that you've reached that limit. 

Of course I could be entirely wrong. What output does the "df" commands give you?

---

