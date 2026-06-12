---
title: "How to find / partition?"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-07
Upgrade to Jaunty caused many problems, so I'm installing Jaunty from the live CD.

I want to keep my partitions the same, so I use the manual feature on the installation screen.

The next step requires me to identify the / partition.  When I first installed Ubuntu, I did not write anything down.

Is there a way I can figure out (from a terminal window, perhaps?) which device (e.g. /dev/sdc6?) contains the / partition?

Using Applications>accessories>disk usage analyzer I can see the size of / and from that guess that it is a certain /dev/sdc6 (the size of which is given from the command sudo fdisk -l), but this seems risky to me.

On the other hand, when I tried installing from the live CD, the partition screen showed one partition (/dev/sdc12) with the label "Ubuntu 9.04".  I imagine that must be because Jaunty already resides on my system.  Does this mean that this is the / partition?  The one labeled Ubuntu 9.04?

Any and all suggestions will be greatly appreciated.

---

### Post by raymondvillain on 2009-06-07
Eureka!

To find the device on which is located the / partition, just use the df command in a terminal.

What a relief!

On my machine the first line is /dev/sdc12 and the mount column says "/" so that is worth knowing.

---

### Post by raymondvillain on 2009-06-07
Went through the motions of installing Jaunty from the live CD.  Tried to keep everything "as is" but reformatted the device with the / folder.  Setup finished without a hitch, but when I restarted, absolutely nothing.  The GRUB loader worked (it is a dual boot setup, also has Windows XP), I choose Ubuntu, hit "ENTER", and then the screen goes blank.  Nothing else happens.

When I boot to the live CD, is there a way I can see the partitions, directories, files, etc. so I know they're still there?

Any hints or suggestions?

Thanks in advance from a desperate linux user.

---

### Post by merlinus on 2009-06-07
After booting from the live cd, open a terminal and then post output of:

```

sudo fdisk -l

```

---

### Post by raymondvillain on 2009-06-07
O. K.!

Here is the output of sudo fdisk -l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b5d9b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x06fab47b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       78053    39338680+   7  HPFS/NTFS
/dev/sdb2           78054      310100   116951688    f  W95 Ext'd (LBA)
/dev/sdb5           78054      156981    39779680+   7  HPFS/NTFS
/dev/sdb6          156982      310100    77171944+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc719

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    5  Extended
/dev/sdc5            2610        5036    19494877+  83  Linux
/dev/sdc6            5037        8133    24876621   83  Linux
/dev/sdc7            8134        8631     4000153+  82  Linux swap / Solaris
/dev/sdc8            8632       28083   156248158+  83  Linux
/dev/sdc9           28084       29056     7815591   83  Linux
/dev/sdc10          29057       30401    10803681   83  Linux
/dev/sdc11              1         196     1574275+  83  Linux
/dev/sdc12            197        2609    19382391   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by merlinus on 2009-06-07
/dev/sdc1               1       30401   244196001    5  Extended
/dev/sdc5            2610        5036    19494877+  83  Linux
/dev/sdc6            5037        8133    24876621   83  Linux
/dev/sdc7            8134        8631     4000153+  82  Linux swap / Solaris
/dev/sdc8            8632       28083   156248158+  83  Linux
/dev/sdc9           28084       29056     7815591   83  Linux
/dev/sdc10          29057       30401    10803681   83  Linux
/dev/sdc11              1         196     1574275+  83  Linux
/dev/sdc12            197        2609    19382391   83  Linux

It would seem that ubuntu / is on one of these linux partitions.  Part of the problem is that obviously something got changed upon your reinstall. since the partitions are not in order.

Did you install / in the first partition on sdc?  If so, then it appears to be sdc11.

You could manually mount sdc via the terminal in the live cd, and run

df -h 

which will show what is /.

---

### Post by raymondvillain on 2009-06-07
How to mount from a terminal window?

What does it mean when it says

Disk /dev/sdc12 doesn't contain a valid partition table

??

Did I make a mistake formatting?

One of the options in formatting is the partition table.  I omitted that since I thought it would overwrite all my other partitions.  Is that correct?

---

### Post by merlinus on 2009-06-07
What does gparted show for sdc?

---

### Post by raymondvillain on 2009-06-07
Gparted shows six columns:  Partition, File System, Size, Used, Unused & Flags.

/dev/sdc11 ext3 1.50 Gib  103.09 MiB  1.40 GiB
/dev/sdc12 ext3 18.48 GiB  2.38 GiB    16.10 Gib
/dev/sdc5  ext3  
/dev/sdc6  ext3  23.72 GiB  363.74 MiB  23.37 GiB
/dev/sdc7  linux-swap
/dev/sdc8 ext3
/dev/sdc9 ext3
/dev/sdc10 ext3

I didn't type everything in, but the sizes all make sense.  The flags column has no entries.

What should I be looking for?

If I select /dev/sdc6 (with a right click) and then click on "information", it says the device is unmounted.

How should it be mounted?  I mean, what are the commands from a terminal window?

---

### Post by merlinus on 2009-06-07
You might try mounting this way:

```

sudo mount -a

```

If that does not work, then:

```

sudo mkdir /media/sdc6
sudo mount /dev/sdc6 /media/sdc6

```

See what happens....

---

