---
title: "Fixing the grub"
date: 2008-11-23
forum: General Help
---

### Post by plaquex on 2008-11-23
hiho,
I'm pretty new to linux... I had a windows partition installed on hd0,0 and my linux is installed on hd0,1(15gb for / (dev/sda1) 1gb for swap(dev/sda2) and 142gb for /home(dev/sda3)).. at least I think that is what I figured out in the last two hours...
I tried to fix my grub with serval howto's but I didn't manage to fix it.. Right now I'm on a knoppix live system and I don't really know what to do..
any solutions or more information needed ?

---

### Post by Dr Small on 2008-11-23
What exactly is the problem?

---

### Post by plaquex on 2008-11-23
The problem is that I can't boot into my linux anymore and that the grub-fixing-howto's didn't work for me...

---

### Post by Dr Small on 2008-11-23
Could you post a copy of /boot/grub/menu.lst ?

---

### Post by plaquex on 2008-11-23
Sure.

1 
2  default 0
3  timeout 30
4  title=Gentoo Kernel 2.6.27
5  root(hd0,1)
6  kernel /boot/kernel-2.6.27 root=/dev/sda2 ro
7
8  title=Gentoo Kernel 2.6.25
9  root(hd0,1)
10 kernel /boot/kernel-2.6.25 root=/dev/sda2 ro
11
12 title=Gentoo Kernel 2.6.24
13 root(hd0,1)
14 kernel /boot/kernel-2.6.24 root=/dev/sda2 ro
15
16 title=Windows XP
17 rootnoverify (hd0,0)
18 makeactive
19 chainloader +1

---

### Post by Slim Odds on 2008-11-23
> **plaquex said:**
> Sure.

1 
2  default 0
3  timeout 30
4  title=Gentoo Kernel 2.6.27
5  root(hd0,1)
6  kernel /boot/kernel-2.6.27 root=/dev/sda2 ro
7
8  title=Gentoo Kernel 2.6.25
9  root(hd0,1)
10 kernel /boot/kernel-2.6.25 root=/dev/sda2 ro
11
12 title=Gentoo Kernel 2.6.24
13 root(hd0,1)
14 kernel /boot/kernel-2.6.24 root=/dev/sda2 ro
15
16 title=Windows XP
17 rootnoverify (hd0,0)
18 makeactive
19 chainloader +1

And how, exactly, does this relate to Ubuntu?

---

### Post by Dr Small on 2008-11-23
Looks to me that root should be /dev/sda1, like this:
```
kernel /boot/kernel-2.6.25 root=/dev/sda1 ro
```

---

### Post by plaquex on 2008-11-23
Not at all. I know...
I just found threads about people having troubles with their in here and thought that you guys could help me :/

---

### Post by plaquex on 2008-11-23
> **Dr Small said:**
> Looks to me that root should be /dev/sda1, like this:
```
kernel /boot/kernel-2.6.25 root=/dev/sda1 ro
```
Seems to be working until some point.. I had to change the line above with root(hd0,1) to root(hd0,0)..
Now I get the following error message..
* Checking root filesystem ...
fscheck.ext3: Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and now swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
   e2fsck -b 8193 <device>
* Filesystem couldn't be fixed :(                          [ !! ]
Give root password for maintenance
(or type Control-D to continue):

Well.. I installed my filesystem with ext3 btw.. oO

---

### Post by Dr Small on 2008-11-23
Looks like the filesystem is corrupted.

---

### Post by plaquex on 2008-11-23
Well, I can still mount my home directory with access to all my files.

---

### Post by pastalavista on 2008-11-23
Download [SuperGrubDisk]("http://www.supergrubdisk.org/"), burn it to CD, boot from it and select the type boot you want. It'll do the rest.

---

### Post by caljohnsmith on 2008-11-23
Please post the output of the following commands:
```
sudo fdisk -lu
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```

---

### Post by EnGorDiaz on 2008-11-23
maybe my post in my sig could help you out with the restore of grub?

---

### Post by plaquex on 2008-11-23
> **caljohnsmith said:**
> Please post the output of the following commands:
```
sudo fdisk -lu
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```

sudo fdisk -lu:
Platte /dev/sda: 250.GByte, 250059350016 Byte
255 Köpfe(heads), 64 Sektoren/Spuren (sectors), 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 x 512 = 512Bytes

Gerät  boot. Anfang Ende Blöcke Id System
/dev/sda1 * 156248190 185566814 14659312+ 83 Linux
/dev/sda2   185566815 187542809 987997+ 82 Linux Swap / Solaris
/dev/sda3   187542810 488392064 15024627+ 83 Linux


sudo grub:
brings me into the grub bash.

root(hd0,1):
Filesystem type unkown, partition type 0x82
( root (hd0,0) <- seems to be working )
setup(hd0):
...


root (hd0,0):
Filesystem type is ext2fs, partition type 0x83

setup (hd0):
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot"grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grubd/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

---

### Post by caljohnsmith on 2008-11-23
One thing I notice is that sda1 starts at ~80 GB into your HDD, and the space before that is unallocated. Do you want to use that 80 GB of space? If so, I would suggest adding a partition to that space before proceeding to fix Grub, because adding a partition there will change how you need to fix Grub. Or you could start over, set up your partitions to use the whole HDD, and reinstall. Let me know what you decide to do, or if you would like further help with your partitions.

---

### Post by plaquex on 2008-11-23
Yeah, I had a winxp installed before and I tried to reinstall it and that ****** everything up... Would be cool if I could have a winxp partition again :)
And yes, please help me with that.. I seriously don't know what to do anymore... I'm already trying to fix everything for about 2-3hours... :(

---

### Post by caljohnsmith on 2008-11-23
If you are going to install XP at some point, I would strongly recommend doing that before installing Ubuntu to make things easier. How about looking at this guide:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

So you can first use "gparted", i.e. Ubuntu's partition editor to set up all your partitions first, including making a primary NTFS partition for XP. Then you can make two partitions for Ubuntu, one for the main file system and one for swap. Or you could make an additional partition for Ubuntu exclusively for your /home directory, or all your personal files. That's usually a good way of doing it. If you have specific questions, let me know, but the above guide should be a good start.

---

### Post by plaquex on 2008-11-23
Yay! It seems like that everything is working again :D Thanks for the hint with gparted :> that solved my whole problem with installing windows and fixing the grub! And also thanks for the hint with the supergrub thing! :D And also thanks to everyone that tried to help me =)

---

