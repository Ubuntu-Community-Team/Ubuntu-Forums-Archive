---
title: "Can some tell me the meaning of this"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by noelc on 2009-04-16
Last week while trying to create a dual boot I believed I wiped Windows accidentally. No problem had all data back up. This week I tried to install XP in "Virtual" but the XP install process kept hanging (Haven't figured that one out yet). Anyway while playing I noticed some "Window files" which I thought were gone so I performed a fdisk 1 and got this

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris
noel@noel-desktop:~$ 

Can someone tell what this means please??

---

### Post by ahbart on 2009-04-16
There is no windows partition on this disk. 
/dev/sda1 is the root partition (around 146Gb?) and /dev/sda5 is your swap partition.

So I don't know where you saw this windows files.

---

### Post by mozetti on 2009-04-16
It means you have 1 primary partition and 1 extended partition; the extended partition contains a logical partition you're using as Linux Swap and it uses the entire extended partition.

Nothing out of the ordinary, really, except that you really don't need the extended partition. A hard drive can only have 4 primary partitions, so if you want more than 4 partitions then you create an extended partition to hold additional logical partitions. In your setup, you could just have 2 primary partitions - 1 for Linux (root, home, etc) and 1 for Linux Swap. You definitely don't have a "windows" partition on that drive.

If you do any re-arranging/re-installing, then you should consider making a separate partition for /home.

---

### Post by StuartN on 2009-04-16
> **noelc said:**
> ```

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris
```

You have two partitions - partition 1 is a bootable Linux partition, extended partition 2 contains partition 5, which is a swap partition. Partion 1 is about 150 million blocks and partition 5 is about 6 million blocks (and extended partition 2 is a tiny bit bigger because it contains partition 5 and some data about partition 5).

---

