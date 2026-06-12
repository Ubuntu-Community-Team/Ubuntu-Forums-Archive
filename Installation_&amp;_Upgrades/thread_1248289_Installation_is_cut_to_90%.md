---
title: "Installation is cut to 90%"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by lricardorl on 2009-08-24
Hi all!!.

First I have a machine Optiplex 170L with cpu P4 to 3.0 ghz, 1.5 gb of ram and 1.2 gb  of swap, Hd of 250 gb.I have the disk partitioned as follows:

sk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1df21df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       27970   182723310    f  W95 Ext'd (LBA)
/dev/sda5            5223        7572    18876343+   7  HPFS/NTFS
/dev/sda6            7573       16710    73400953+   7  HPFS/NTFS
/dev/sda7           16711       16971     2096451    b  W95 FAT32
/dev/sda8           16972       22192    41937651    6  FAT16
/dev/sda9           22193       22354     1301233+  82  Linux swap / Solaris
/dev/sda10          22355       23225     6996276   83  Linux
/dev/sda11          23226       24034     6498261   83  Linux
/dev/sda12          24035       25128     8787523+  83  Linux
/dev/sda13          25129       25999     6996276   83  Linux
/dev/sda14          26000       27119     8996368+  83  Linux
/dev/sda15          27120       27970     6835626   83  Linux

Well, my problem is thist: I cannot install ubuntu in any partition ubuntu in any partition that is not attached to the swap or the last partition windows (sda7), sda8 is empty. The point is that i could install a modified version of ubuntu, but after i try to install ubuntu in the follow ( or any)  partition (differents versions and also derives), and  cut to 90%, gives no message (or register) is interrupted only :(:|. I have experience in Installations of Linux, but this error is new. But, i can install differents distos Linux in the other partitions!. Where is the problem??. I read papers of partitions and file system, also i have read in forums: ubuntu download packages during installation, is true, but cut after that :|. With a distro installed i see the content and missing files in the folder dev and files in the folder etc.
Its a bug if ubuntu?? :|:|.can not seem to coexist with other distributions, but is first installed :(

I need help!, As a side note: review of all tests that use ubuntu.

---

### Post by stlsaint on 2009-08-24
well yes ubuntu can co-habitate a system with other distros...i have run fedora with ubuntu, teste mint, mepis etc...now first off could you explain what setup you have...looks like you have aloth of 17+ GB partitions...which leaves alot to wonder about conflictions you may have internally? care to elaborate on your error?

---

### Post by lricardorl on 2009-08-27
well, i have installed Fedora, Slackware, Debian and others, and i tryed 10-12 times in the partition sda11.

Greetings

---

