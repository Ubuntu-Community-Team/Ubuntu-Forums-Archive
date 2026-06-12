---
title: "Need to add space to root partition"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by timczer on 2006-01-05
I know I have read several posts on similar subjects, but when searching I have not found one the specifically applies here, or doesn't leave me unsure of what to do.  I need to be sure as I can not screw up my install as I have important work info (server and such) running and can't afford to have to redo it at this time (not cost, but time).

Here is what I have:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9756    78365038+   7  HPFS/NTFS
/dev/hda2            9757       13151    27270337+   c  W95 FAT32 (LBA)
/dev/hda3           13152       15701    20482875    c  W95 FAT32 (LBA)
/dev/hda4           15702       19458    30172590+   5  Extended
/dev/hda5   *       15702       15766      522081   83  Linux
/dev/hda6           16466       16668     1630566   82  Linux swap / Solaris
/dev/hda7           16669       19458    22405162+  83  Linux
/dev/hda8           15767       16465     5614686   83  Linux

My root partition is hda8.  I would like to add some space to it as I am at about 60% full and have some more things I need to add.  I don't want to be in danger of running out of space later.  According to gparted, the order of partitions on the hda4 extended partition is hda5 (boot), hda8 (/root), hda6 (swap), hda7 (/home). 

I am not sure why, but I put a lot of space (it looks like 1.5 gigs) in the swap partition.  Can I delete this partition, grow my root partition into this empty space, then shrink the hda7 partition by a gig and put the swap file at the end of the disk?  Then all I should have to do is change fstab to reflect the new location of the swap file?

Do I need the swap file at hda6?  From a previous install of Ubuntu on my b drive I have a swap file located at the beginning of that drive as well.  This shows up in my fstab.  When I look at my resources in gnome-monitor, it shows 2.5 gigs of swap, which is what these two partitions now contain.  If I eliminate the hda6 partition, I would still have swap on hdb1?


And can this be done without losing info on the /home partition?

---

### Post by timczer on 2006-01-05
Alright, after additional searching on other threads I bit the bullet and gave it a try.  Everything worked out well.  For anyone who might read this on their own search, there were a couple of points of learning that might help them.

The first thing I did not expect, is that when I deleted the swap partition on hda6, the partition table changed, reflecting the former hda8 partition was now labled as hda6.  This was it's actual location before, but during my initial setup somehow it was labeled as hda8.  (When you run fdisk -l to get the set up of your disk, it will tell you that the labeled partitions are not necessarily in the order shown on the screen.  This is good information to know as if this is the case you may have similar issues to what I had).   This required me to remount the drive in order to get the proper partition table to load before I could then resize the root partition (now hda6).  This went fine.  

The next thing to I learned, was that clearly I could now not just boot back into Breezy, as my root partition had moved.  I had to do a quick edit on the grub screen to point it to the right partition to find /root.  After that, It booted right back to Breezy, and I have the new space in my root partition.  Yeah!

---

### Post by anil_robo on 2006-01-05
Thanks for posting this. I was in the same situation as you were, but I chose to reinstall Ubuntu. That fixed some broken packages and some other errors as well! :)

---

### Post by chrism7 on 2006-01-06
Did you use gparted to resize root while in ubuntu?  I was looking the other week to resize my root (shrink, not grow though) and from memory gparted wouldn't let me do anyhting to it while it was mounted, and I don't think I could unmount it conisdering that it was in use.  I'm at work though, not in front of the PC so can't try this now to see.  I have root and home on the one partition, and I want to separate them, so need to create some space for this.

EDIT: Don't worry, the noob in me is coming out.  I remembered I'd read somewhere else what to do - use a Live CD.

---

### Post by timczer on 2006-01-06
Exactly, you have to boot off a live cd that has gparted or qtparted and resize from there.  Definitely read the many threads on resizing partitions to make sure you are comfortable that you aren't going to lose anything before you start.

---

### Post by foxiness on 2006-01-13
other idea i have is with tar ...

1- backup everthing then restore it on new one "HD or Partition"

2- something like on XP move the Documents to other "HD or Partition" .

now i have this problem and i saw when i try to drag-drop anything with alt link to ,and may this will help.

---

