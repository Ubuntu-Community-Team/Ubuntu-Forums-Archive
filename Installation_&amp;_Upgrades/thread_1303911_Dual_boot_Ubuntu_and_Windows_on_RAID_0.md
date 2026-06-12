---
title: "Dual boot Ubuntu and Windows on RAID 0"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by loopzilla on 2009-10-28
Hello !

I have a big problem with installing Ubuntu 9.04 to RAID0 array.

The first problem is that Live CD doesn't see RAID0.

So I installed dmraid package. Run dmraid -ay.
And raid0 has been detected and all partitions was visible.
Then tried to install using graphic UI, but it crashed on configuring grub stage :(
So I installed only system without grub as described in article:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

And tried to configure grub...

But grub don't want to boot, he fails with Error 17 :(

The MAIN question is:

**How GRUB knows that hd0 is a RAID0 ARRAY ?**

File /boot/grub/menu.lst is located on ext3 partition (that located on RAID0 array).
So GRUB needs to mount this raid0:ext3 partition to read his configuration ...

When Windows installs he requires driver for RAID on floppy.
In loaded Linux we can load dmraid module that will detect them.
**But GRUB ?**

I suppose that this is a separate binary module that located in MBR and able to mount popular file systems such ext2, ext3, etc to run system loaders from them.
And it can use only BIOS functions (interrupts).
Probably he see two separate disks, and tries to mount first half of RAID array  !?

Thanks !

---

### Post by Tomatosoup on 2009-10-28
I think you can forget fakeRAID support... There are people who whish it, but it still hasn't been granted... Noone really seems to listen. Even GRUB2 doesn't support BIOS-RAID0.

Even the much criticised Vista has fakeRAID support.

Bought a brand new Dell XPS 430 this year. Had to install Ubuntu on an external hard drive.

Tried some commandline tricks, but to no avail.

---

### Post by Tomatosoup on 2009-10-28
Though you could make it none-RAID. Of course you first have to backup your data, if you have something on it already. ;)

---

### Post by niite on 2009-10-28
I have no clue why anyone would want to run RAID0 anyway..  if a drive corrupts or has a problem your screwed with the whole array.  I'm not that concerned with performance..  so I said no to RAID when i got my new computer..  I use one drive for my windows install, and second drive for linux.. and it keeps me quite happy. If i really wanted to get serious, I'd install both os's on seperate partitions on one drive, and keep all my data on the other..  maybe tormorrow.

---

### Post by Tomatosoup on 2009-10-28
Masturbating blinds people, but people still do it! ;) ;)

---

### Post by niite on 2009-10-29
> **Tomatosoup said:**
> Masturbating blinds people, but people still do it! ;) ;)

LOL - no kidding.

---

