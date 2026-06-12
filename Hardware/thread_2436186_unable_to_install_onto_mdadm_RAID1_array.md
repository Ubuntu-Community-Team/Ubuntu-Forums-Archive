---
title: "unable to install onto mdadm RAID1 array"
date: 2020-02-01
forum: Hardware
---

### Post by oldgeek2 on 2020-02-01
this has been for several generations ( possibly all of 'em? )
and last I checked was on both UbuntuStudio.org AND Ubuntu Server
( which indicates it is actually across all editions )
( & also CentOS, just for context..., which I found astonishing )

What I want to do is to prep a RAID1 array, off the LiveDVD,
get all the partitioning right, etc,
get all the /dev/md/home /dev/md/ubuntu-root-dev /dev/md/ubuntu-root-minimal /dev/md/tmp  .. etc.
stuff set up,
get the filesystems set up the way I want,
with tune2fs setting up reasonably-frequent fsck
( rural people get LOTS of blackouts:
there is a place just south? of me that got over 140 blackouts *last year*,
so trashed filesystems is too damn normal, hereabouts,
& yes I've got a UPS, but most don't )

& then simply install into it.

Yes I know that Grub2 may require v 0.90 RAID1,
instead of v 1.2 mdadm instantiation,

I simply can't understand why no-one does this
( from what I've read, SSD's simply don't give any SMART warning:
they just spontaneously pop.
Given that, RAID is the ONLY method for protecting one's system's availability
from that! )

Anyways, I'm requesting that mdadm be IN the install-system,
that the install-system be capable of installing into RAIDn ( correctly set up ),
that it be capable of having RAID1 /boot
that it be capable of accepting such a set of already-prepared partitions
( OpenBSD-style dividing filesystems to make some categories of attacks impossible )
and that it be set up to automatically use whatever spares are available/prepped...

1 reason I'm asking this is a peculiar flakyness
( that cost me lots of white hair & cost a friend their brand-new Windows license )
on many Asus motherboards:
it used to be that they had the safe version of "BIOS Save & Exit" primary,
but not for the last ?decade?

Instead, the default option is to load "optimized" defaults,
and whatever damn "optimizing" it does,
makes some hard-drives *intermittently exist*.

Reboot & one has disappeared.

If you don't know that the fix is to go and short the bios-zeroing-jumper,
then re-set-up the BIOS, with NO optimization,
you will get white hair like me!

With self-healing-RAID, however,
even such problems would only reduce-reliability,
instead of show-stopping everything,
until the bizarre "optimization" was countered.

Also had a new NVMe lose some portion of it, for no reason I could discern...

Haven't reinstalled my system yet, after that ( was a few days ago ).

RAID1 would make my life better,
& having it available right in the install, instead of having to fight it into an already-installed Ubuntu would be kinder.

Anyways, Thanks in advance, for whatever results from this, even if nothing:
always keep positive, right?

( :

---

### Post by TheFu on 2020-02-04
The way I'd add RAID1 to an OS LV is to use LVM at install time, then post-install, resize the LVs to what I want (which is always necessary!), then add RAID1 through LVM for each LV.  The command used will be 
```
sudo lvconvert -m1 .... 
```  
Remember, with LVM allocate the storage you need for the next month or two, don't allocate all the VG storage or you'll remove the flexibility to change LVs, use snapshots, etc.  A fully allocated VG storage area defeats most of the usefulness of LVM.  With SSDs, it is smart to leave 20% unused, unallocated, so the SSD controller can use that extra storage for wear levelling.

My non-RAID LVM setup: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) with size explanations.

The EFI boot areas cannot be RAID. To get around that lack of redundancy, you can manually rsync those files after every new kernel ... or just do it automatically daily. As long as that task doesn't happen while the source area is being modified, it should be fine. If something bad happens to the original, use the EFI booter and select the alternate EFI boot area.  I've not tried this, but it should work.  People clone it to USB storage and boot off that to thwart the evil-maid attack.  Should work, but I haven't tried it myself.

BTW, I doubt a Win10 license has been lost.  My Asus laptop has the license burned into the BIOS somewhere, though i've never used it.

---

