---
title: "Partition table was changed unintentionally"
date: 2008-07-20
forum: General Help
---

### Post by kcirtap on 2008-07-20
I had Windows XP installed on a 30GB partition. Arch Linux installed on a 35-40GB partition for the rootsystem / and 15GB for /home and a swap space 3,5GB.

Everything worked ok, I was using my OS and all, but I wanted to use the 230GB unpartitioned space left on my harddrive. I only had a Windows XP CD so I thought I could use that. Well, when I booted the Windows XP CD all partitions were in place it seemed, and there was the unpartitioned space. I created a partition in that space, then when the partition was done, all partitions were a mess. The freakin XP-CD didn't even ask me if I wanted to do the change, so now I cannot boot my computer.

Now I wonder if there's a way to undo these changes. Maybe it's possible to "repoint" the partitiontable to the right place somehow?

Thankful for any help. I haven't done a thing since I made this change, so IMO it should be possible.

If this is of any help, this is how it looked if I remember right.

/dev/sda1 Windows XP
/dev/sda2 rootfilesystem / Arch Linux (ReiserFS)
/dev/sda3 Swap space
/dev/sda4 /home (ResierFS)

---

### Post by danwood76 on 2008-07-20
It is possible to rebuild partition tables but it can be a little difficult depending on what the windows CD did to the partition table.

There is a piece of software availble on the Ubuntu live CDs repositories that can do an auto scan for lost partitions.
The app is called testdisk, you will need an internet connection as the repo is online.

Boot into the live CD and run this in a terminal to install:
```

sudo apt-get install testdisk

```
Then to run testdisk run:
```

sudo testdisk

```
Within that you will want to select an Intel partition structure and then run analyse to search for the lost partitions.
It sometimes helps if you do a deep scan after the initial scan then get it to save the partitions it found.

Normally you will be able to get most of your data back but i would bet that anything on the first partiton of the disk will be ruined.

In the future you should probably use something like Gparted within ubuntu to re partition as micorsoft products are a little lame.

---

### Post by kcirtap on 2008-07-20
Thank you. I have one problem though, it doesn't find the testdisk package. I cannot really boot the GUI because my graphics card has some issues with Linux in general. But i've booted into the CD CTRL + BACKSPACE out of X and entered console mode. Can that be the reason why it doesn't find the package? If so, can I add some reps?

edit:
Nevermind, I found the package now.

---

### Post by Yannick Le Saint kyncani on 2008-07-20
Testdisk is in the universe section of the repositories.

A line like that :
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
In /etc/apt/sources.list should do.

sudo nano /etc/apt/sources.list   to edit the file
sudo apt-get update
sudo apt-get install testdisk

---

### Post by danwood76 on 2008-07-20
Yes you can add the extra repos, it should be located in the universe repo.

To add this open up the config file:
```

sudo nano /etc/apt/sources.list

```
and add the following two lines to the bottom:
```

deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

```
Then we need to update the software list:
```

sudo apt-get update

```
And then you should be able to get the software package:
```

sudo apt-get install testdisk

```

---

### Post by kcirtap on 2008-07-20
Alright, i've analyzed the disc /dev/sda, 320GB. Before I started analyzing, the following table was shown (just a FYI):

[I]HPFS - NTFS   0 1 1 3823 254 63  61432497 [Windows]
Linux         3824 0 1 5647 254 31   29302528
Linux Swap    5648 0 1 6073 254 45 6843672
Linux         6074 0 1 10328 253 31 68356480[/I]

After the analyze is done, about the same thing is shown, execept that two lines are added (additional Linux and swap). In other words, this is how it looks like now in testdisk:

[I]HPFS - NTFS   0 1 1 3823 254 63  61432497 [Windows]
D Linux         3824 0 1 5647 254 31   29302528
D Linux Swap    5648 0 1 6073 254 45 6843672
D Linux         6074 0 1 10328 253 31 68356480
D Linux 35695 0 1 38794 254 63 49801500
D Linux Swap 38795 0 1 38912 254 63 1895670[/I]

What am I supposed to do now?

---

### Post by danwood76 on 2008-07-20
The D by each partition means its been deleted.

You need to change each partition you want to save them as primary or extended partitions. (it should set the primary and extended automatically)
Its been a while since I used this app so Im not 100% sure.

There is quite a bit of unpartitioned space on your drive which I assume should be what you expect.

---

### Post by louieb on 2008-07-20
Did the same thing - used XP to create a partition in unallocated space. But all it did was screw up the boot code in the MBR,  my partition table was fine.

To fix just had to put the grub ipl code back in the MBR.

Just wondering what your partition table looks like  to find out run ```
sudo fdisk -l
``` (lowercase L)

---

