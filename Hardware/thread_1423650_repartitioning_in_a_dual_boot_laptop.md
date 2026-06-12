---
title: "repartitioning in a dual boot laptop"
date: 2010-03-06
forum: Hardware
---

### Post by bob12564 on 2010-03-06
I need some beginner help.

I just added Karmic/9.10 to my Toshiba laptop in a dual boot with the existing Windows XP.  I allowed the Ubuntu installer choose the partition sizes but I now think they're wrong for my needs.  I've read that it's possible to boot from the live CD and use Gparted to sometimes safely rearrange partitions, but the procedure is going over my head. Here's what the installer did to my 60g drive:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe905e905

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4294    34491523+   7  HPFS/NTFS
/dev/sda2            4295        7296    24113565    5  Extended
/dev/sda5            4295        7166    23069308+  83  Linux
/dev/sda6            7167        7296     1044193+  82  Linux swap / Solaris

The Windows XP partition is using about 13 gigs according to the disk usage analyzer tool and I can't see allocating 35g to it.  I intend to use Ubuntu and keep Windows as a fallback.  I would prefer to lower the Windows partition to 25g and bring the Linux partition up to 35g.  

I was able to run Gparted and figure out how to simulate the changes without applying them permanently.  I reduced the Windows partition but I was left with unallocated space that I couldn't add to the Linux partition.  

Can this be done and will it leave me with a corrupted Windows boot partition or a corrupted Grub?  If it can be done safely, can someone walk me through it in beginners language?

Thanks for the help!

---

### Post by soul_rebel on 2010-03-07
You are right about gparted from the live cd, it's the way to go. A few bad things could happen when you resize and move partitions, but allmost all of them can be solved and probably things will just work.

I think that after shrinking windows you have to enlarge the extended partition, then gparted shoul let you resize ubuntu partition too. An extended partition is a partition with many partitions in it. It's there for historical reasons...

Another option could be to reinstall ubuntu and choose the manual partitioning, but that would wipe off your existing ubuntu.

---

### Post by bob12564 on 2010-03-07
I used Gparted to first simulate the shrinking of the primary partition which contains Windows XP.  That left an unallocated space between the primary and extended partitions.  So far so good.  Then I tried to bring the unallocated space into the extended partition and that didn't work or, maybe more correctly, I couldn't figure out how to do it and that's where I need help.  I then tried to create a partition from the unallocated space thinking I could then move it to the end of the extended partition and then join it to the existing extended partition.  But it would only allow me to create it as a another primary partition and I didn't think that was right.  I ended the simulation.  The Gparted help isn't detailed enough to walk me through this.  I still need some pointers.

Thanks!

---

### Post by bob12564 on 2010-03-07
Got it!

Even though I was running under the live CD the Linux partitions on the hard drive were locked.  I found something in the Gparted menus called "swapoff" which unlocked the Linux partitions.  Once that was done it was easy to do what I wanted.  For anyone else with the need, here's how you do it: First shrink the primary partition which has Windows XP in it.  That leaves you with unallocated space between the primary and extended partitions.  You can then use the Gparted GUI to stretch the left bound of the extended partition to the left to add the unallocated space to the extended partition.  Then you use the GUI again to drag the Linux partition to the left bound of the extended partition.  Gparted does the rest.  It actually worked!  I am very impressed.

---

### Post by soul_rebel on 2010-03-08
Yes the live cd automatically mounts any swap partition it finds, in case it runs out of ram.

---

