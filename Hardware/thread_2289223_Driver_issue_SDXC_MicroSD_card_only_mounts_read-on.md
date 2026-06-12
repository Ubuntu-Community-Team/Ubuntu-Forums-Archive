---
title: "Driver issue SDXC MicroSD card only mounts read-only. Switch 10 Bay Trail chipset."
date: 2015-08-02
forum: Hardware
---

### Post by halfnote52 on 2015-08-02
SDXC MicroSD card only mounts read-only. Acer Aspire Switch 10 Bay Trail chipset. Xubu 15.04.   

gparted won't touch it,  remount to rw and wipefs won't have anything to do with it.  They all say "read-only file system."   In fact, (ro) shows up in dmesg immediately after the info upon inserting. I would LOVE to make this thing work properly in read/write and I'm almost positive it's a driver issue.

__________________________________


Okay, so here's the details:   I have a brand new MicroSD SDXC card.  64 GB Verbatim.  

**The card itself works fine.   **

To back up this assertion:  1. I've used it (r/w) in Windows on the **same machine**.  2. I've used it in Xubuntu 15.04 on an Aspire Switch 11, and a couple **other machines**, and **it opens read-write**. 

The problem is NOT the exFat fuse/utils. They're installed. I know this because the OS on the Aspire 10 is a live remaster I made of the one on on the (working) Switch 11. I also double-checked to rule out any remastering weirdness.

The problem is ALSO not the exFat filesystem, because I partitioned and reformatted it under Windows to be FAT32. **This also works fine on the other 15.04 machines**. 

I've narrowed it down to either a driver issue or a settings quirk, and would appreciate any guidance anyone could provide. 

Thanks!


**[SIZE=1]P.S. Please do not suggest that I check the locking switch. This is a MicroSD card going into a MicroSD slot. There is no locking switch, and if there were, I'd like to think I'd've already thought to check that[/SIZE]**. :wink:

---

### Post by TheFu on 2015-08-02
[https://askubuntu.com/questions/410776/unknown-filesystem-type-while-mounting-sdxc-card](https://askubuntu.com/questions/410776/unknown-filesystem-type-while-mounting-sdxc-card)
Also, there appears to be a kernel bug with certain card-reader chips. [https://bugzilla.kernel.org/show_bug.cgi?id=73241](https://bugzilla.kernel.org/show_bug.cgi?id=73241)

Gotta love those proprietary file systems!

---

### Post by halfnote52 on 2015-08-03
Thanks! Though, truth be told, the first link isn't the issue. I've already checked on that. The bugzilla article might be promising, although since I am running it from live, currently, the initramfs/reboot part might require some... tweaking.

---

