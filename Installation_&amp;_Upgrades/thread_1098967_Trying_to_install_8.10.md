---
title: "Trying to install 8.10"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by Derp on 2009-03-17
So I tried installing Ubuntu today.

Problems thus far:
After copying all the files over to a new partition, screen goes black and I get the terminal, a flickering screen about 7 or 8 times and then a message to say that the service restarted 8/9 times in 90 seconds. 
For some reason, Ubuntu does not seem to like my Nvidia graphics card. 
(Can't remember off the top of my head, but the message was "Restarted X amount of times in 90 seconds)

I've tried doing dpkg-reconfigure xserver-xorg whilst in the terminal after the installation to see if that would work, and didn't. 

So after that, I tried rebooting into windows through grub, only to find that after I delete the partition with 8.01, it deleted grub, and my current installation hasn't actually configured grub yet (there is no grub in /boot/ in the root)

What a day, huh? Any help would be appreciated (as I scour the forums looking for clues)

---

### Post by LegendofTom on 2009-03-17
You copied your files over? From what?

---

### Post by Derp on 2009-03-17
> **LegendofTom said:**
> You copied your files over? From what?

Woops, I meant *after ubuntu finished copying files from the installation disk to the new partition (new partition that I made in the Partition Manager). 

It's a new install, one that isn't working.

---

### Post by taurus on 2009-03-17
Well, you could list the spec of your machine, especially the nvidia graphic card.  

And did you remove Ubuntu from your harddrive, causing GRUB to give you an error when you try to boot windows?

---

### Post by Derp on 2009-03-17
> **taurus said:**
> Well, you could list the spec of your machine, especially the nvidia graphic card.  

And did you remove Ubuntu from your harddrive, causing GRUB to give you an error when you try to boot windows?

If by removing Ubuntu you mean deleting the partition with that on it before I reinstalled it with 8.1, then yes.

Intel Pentium D (3.2GH/z, can't remember if it's a springfield or the other one)
4GB DDRII RAM
Nvidia 7900GS BFG 
HDD's in order of booting:
Maxtor 80GB (SATA) (this is the HDD with Ubuntu on it)
WD 1TB (SATA)
Seagate 500GB (SATA)
WD 200GB (IDE) 
WD 320GB (IDE)

---

### Post by taurus on 2009-03-17
So you are running intrepid (8.10) from your harddrive now.  Did you install a driver for your nvidia graphic card?  Try booting into recovery mode from GRUB menu and pick the xfix option to see if that fixes your X server, letting you log into Gnome again.

---

### Post by Derp on 2009-03-17
> **taurus said:**
> So you are running intrepid (8.10) from your harddrive now

No no no, I'm running through the Live CD right now

---

### Post by taurus on 2009-03-17
One option is to remove Ubuntu LiveCD so you can boot from your harddrive.  But at the GRUB menu, pick recovery mode and xfix to see if that fixes your X server.

---

### Post by Derp on 2009-03-17
> **taurus said:**
> One option is to remove Ubuntu LiveCD so you can boot from your harddrive.  But at the GRUB menu, pick recovery mode and xfix to see if that fixes your X server.

Problem: Grub brings up an Error 17, which I've tried to fix, but found there is no GRUB folder in /boot/ on the partition which I've installed linux on.

---

### Post by taurus on 2009-03-17
You don't need a separate /boot partition.  You can have one / (root filesystem) that holds /boot (and your $HOME--/home).  From Ubuntu LiveCD, post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

p.s.  So does Ubuntu ever boot (from harddrive) after you installed (or copies files over from CD to harddrive) at all?  When did you get the flashing screen, couldn't start the X server?

---

### Post by Derp on 2009-03-17
> **taurus said:**
> You don't need a separate /boot partition.  You can have one / (root filesystem) that holds /boot (and your $HOME--/home).  


Oh. Ok.

> p.s. So does Ubuntu ever boot (from harddrive) after you installed (or copies files over from CD to harddrive) at all? When did you get the flashing screen, couldn't start the X server?

No and the flashing screen comes up right after the Ubuntu seems to finish copying all the files from the CD (which I guess is the end of the installation?)
When I boot up and grub starts to load, I get BABEL of Grub (just like in that cartoon that I can't remember the name of)

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42379594

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   42  SFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfec4cf3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   42  SFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75a083ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001   42  SFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1b8c1b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   42  SFS

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c428c42

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        4815    38676456    7  HPFS/NTFS
/dev/sde2            4816        9729    39471705    5  Extended
/dev/sde5            9523        9729     1662696   82  Linux swap / Solaris
/dev/sde6            4816        9522    37808914+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         984     7897056+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)

```

---

### Post by taurus on 2009-03-17
Looks like you installed Ubuntu to /dev/sde6.  Do you remember where you installed GRUB to?

Let's mount it and have a quick look at your installation.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sde6 /media/ubuntu
sudo blkid
ls -la /media/ubuntu/boot
cat /media/ubuntu/boot/grub/menu.lst
```

---

### Post by Derp on 2009-03-17
```

/dev/sda1: UUID="2AE8ABB0E8AB78A9" LABEL="GREED" TYPE="ntfs" 
/dev/sdb1: UUID="1E04167E0416595B" LABEL="AIIGR" TYPE="ntfs" 
/dev/sdc1: UUID="7658023D5801FD1D" LABEL="ZEKERIN" TYPE="ntfs" 
/dev/sdd1: UUID="0E1C45A71C458B23" LABEL="AGWE" TYPE="ntfs" 
/dev/sde1: UUID="1028944828942EAA" LABEL="OBYETM" TYPE="ntfs" 
/dev/sde5: UUID="ea8a5251-5f96-45e9-9044-bed6b4aa8168" TYPE="swap" 
/dev/sde6: UUID="8520b603-44ce-4dd1-bfa0-fa4a07832e99" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdf1: LABEL="SUPER RAGE" UUID="7051-1506" TYPE="vfat"
root@ubuntu:~# ls -la /media/ubuntu/boot
total 3944
drwxr-xr-x  2 root root    4096 2009-03-17 20:00 .
drwxr-xr-x 20 root root    4096 2009-03-17 19:52 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic
root@ubuntu:~# cat /media/ubuntu/boot/grub/menu.lst
cat: /media/ubuntu/boot/grub/menu.lst: No such file or directory

```

---

### Post by taurus on 2009-03-17
Looks like GRUB didn't finish installing on your machine, /dev/sde6, since there should be a directory, grub, in /boot (or in this case, /media/ubuntu/boot).

---

### Post by Derp on 2009-03-17
> **taurus said:**
> Looks like you installed Ubuntu to /dev/sde6.  Do you remember where you installed GRUB to?

Let's mount it and have a quick look at your installation.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sde6 /media/ubuntu
sudo blkid
ls -la /media/ubuntu/boot
cat /media/ubuntu/boot/grub/menu.lst
```

> **taurus said:**
> Looks like GRUB didn't finish installing on your machine, /dev/sde6, since there should be a directory, grub, in /boot (or in this case, /media/ubuntu/boot).
So back to square 1?

IIRC when the installation finished copying the things from the CD it blacked out and went something along the lines of "The something something has restarted 9 times in 90 seconds" after being on the terminal for a minute or two

---

### Post by taurus on 2009-03-17
Maybe if you decide to reinstall, press F4 for safe graphics mode option at the initial screen when you first boot Ubuntu LiveCD.

---

### Post by Derp on 2009-03-17
> **taurus said:**
> Maybe if you decide to reinstall, press F4 for safe graphics mode option at the initial screen when you first boot Ubuntu LiveCD.

Will do, I'll report back when it's done.

---

### Post by Derp on 2009-03-17
Right, reinstalled with safe-mode option turned on, and it's still doing it.

Message: Display server has restarted 6 times in the last 90 seconds, something bad is going on. 
Waiting two minutes to retry on display (illegible, looks like either 10 or IO)

I'll keep it on there until you come back. Could it be the screen that might be the issue?

---

### Post by taurus on 2009-03-17
Maybe the LiveCD doesn't either like your graphic card or your monitor.  You can always try the alternate CD.  It's a text based installer but should be real easy to follow.

---

### Post by Derp on 2009-03-17
> **taurus said:**
> Maybe the LiveCD doesn't either like your graphic card or your monitor.  You can always try the alternate CD.  It's a text based installer but should be real easy to follow.

I'll download that in a second.
In the mean time, is there any way of installing Grub? I'd like to at least be able to go back to the Windows partition should the alt' CD fail on me

*Alternate alternate is that I go back to the 8.04, which almost worked sans the Nvidia drivers and a few other things. I just need to find that CD under this stack of crap...

---

### Post by taurus on 2009-03-17
If you want to remove GRUB so you can boot windows again, here's a link unless you have a window CD.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

