---
title: "help with fdisk"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by mibbster on 2009-09-02
Hi, I have a 40 gig HDD, and have been trying to set up ubuntu on it.  However, due to [bug 423165]("https://bugs.launchpad.net/ubuntu/+bug/423165"), I have not been able to partition the hard drive the way I need it to be partitioned using the partitioner provided in the installer.  I ended up needing to boot into the rescue mode of the install CD, where all I have to work with is fdisk.  I would like to end up with this end result, able to install ubuntu to the places specified.

```

/dev/sda1:
    Type: Primary
    Size: 5G
    Purpose: to install windows on and boot from
    Bootable: yes
 
Partition #2:
  | Type: Extended
  | Size: 28.5G
  |
  +---/dev/sda5:
  |     Type: Logical
  |     Size: 10G
  |     Purpose: /
  +---/dev/sda6:
        Type: Logical
        Size: 18.5G
        Purpose: /home
 
/dev/sda3:
    Type: Primary
    Size: 100M
    Purpose: /boot
    Bootable: yes
/dev/sda4:
    Type: Primary
    Size: 3G
    Purpose: swap space

```


However, due to my unfamiliarity with fdisk, I need someone to walk me through the steps necessary to end up with this, using fdisk.  For example, one of the things I cannot figure out is whether +1K == 1024 bytes, or 1000 in fdisk.  I've also been told its bad practice to start with the first cylinder of the disk.  Is this true?  This is the sort of thing I need people to point out to me, because I'm not used to working with such a low-level partitioner.  Thanks in advance, everyone.  Have a great day! :)

---

### Post by Mark Phelps on 2009-09-02
Suggest you try again by going to distrowatch.com, downloading the current GParted LiveCD ISO, burning it to CD, and booting from that to do your partitioning. 

The bug report you referenced pointed to 8.04 and the current GParted version is a LOT newer than the one bundled with that release.  It's likely that if this WAS a bug, it's been fixed in GParted since then.

---

