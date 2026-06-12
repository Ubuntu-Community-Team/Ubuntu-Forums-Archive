---
title: "Move partitions"
date: 2008-08-20
forum: General Help
---

### Post by ThorX89 on 2008-08-20
Hey guys. I could use some help by now.
Here's what my setup looks like:

```

 Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
                                      Unusable                            24.68
    sda1        Boot        Primary   Linux ext2                          82.26
    sda2                    Primary   W95 FAT32                          419.49
    sda3                    Primary   NTFS             []              16105.10
    sda5        Boot        Logical   Linux XFS                         2146.80
    sda6        Boot        Logical   Linux XFS                         6440.40
    sda7        Boot        Logical   Linux XFS                         2146.80
    sda8        Boot        Logical   Linux swap / Solaris              2146.80
    sda9        Boot        Logical   Linux XFS                        12889.02
    sda10       Boot        Logical   NTFS             []              12880.79
    sda11       Boot        Logical   NTFS             []              23623.01
  Logical   Free Space                        1118.64

```

In English: I've got:
- an ext2 boot primary partition with GRUB /boot
- a FAT32 FreeDOS partition with Firefox and Thunderbird profiles for three users, these profiles are shared between LinuxMint and WindowsXP
- a NTFS partition for Windows XP (C)
- a block of logical partitions for Linux Mint and two data NTFS partitions
- approxim. a gig of free (unallocated) space

Now I've discovered the FAT32 partition is way too small #-o so I would like to "move" the C partition along with the block to the unallocated space and "expand" the FAT32 partition to the 1.5 GB.

At the same time I would like to somehow back up the C partition  (preferably compressed) so that it would be easy to restore it later. 
(I used MS-DOS Norton Ghost to back up my windows partitions, now I would like to replace it with a linux way to do it, if there is any.)

Moreover I've got a /dev/sdb drive with an NTFS partition where there is like 100GB of free space so I could use this for the back up and for the moving of partitions.



I would really appreciate some help here, since I'm practically still a linux beginner and I really need to do this fast (running business) and not to screw it. :cool: THX for any responses.

---

### Post by mgmiller on 2008-08-20
I would suggest using a gparted livecd.  You boot off that and it lets you do all sorts of wonderful things to your partitions.  

It's gui driven and is pretty easy to use.  You can only merge partitions that are next to each other, so sometimes you have to expand stuff in one direction before shrinking it in the other direction.  

Download the .iso version and burn the livecd from that.
Make sure you back up first.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779/&abmode=1](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779/&abmode=1)

---

### Post by mgmiller on 2008-08-20
> At the same time I would like to somehow back up the C partition (preferably compressed) so that it would be easy to restore it later. 
(I used MS-DOS Norton Ghost to back up my windows partitions, now I would like to replace it with a linux way to do it, if there is any.)Yes, there is.  It's called ghost4linux.  Get it here:
[ftp://fedoragcc.dyndns.org/](ftp://fedoragcc.dyndns.org/)

scroll down the page and take the one named: [g4l-v0.26.iso]("ftp://fedoragcc.dyndns.org/g4l-v0.26.iso")  or, you can just click the preceding link and save the file.

This is also a live cd.  It does a lot of things.  Many are not apparent when you first run it.  After it starts up, it shows you all kinds of stuff and then sits at at command line.  Enter "g4l"  without the quotes to start the gui.

This program rescued a bad hard drive for me.  It has a feature to copy a bad hard drive to a good new one.  It takes a long time, but it fixed everything and the new drive booted right into Ubuntu.  The old drive wouldn't even boot.  Amazing!

---

