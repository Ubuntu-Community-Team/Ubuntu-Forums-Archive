---
title: "Seem to have changed my boot partition's filesystem"
date: 2008-10-20
forum: General Help
---

### Post by Yoshidude on 2008-10-20
I have my boot partition, which is also my main Ubuntu partition. Right now, when I try to boot, I get GRUB error 17. So I went into the LiveCD, and although fdisk -l shows me that the partition is a Linux system, gparted says it is unknown, and I can't seem to find it anywhere in the system aside from fdisk. It also gives me superblock errors whenever I attempt to do something about it (like replace the GRUB).

Any advice would be very much appreciated. The obvious answer would be to format, but I'd at least like to see if I could get some of my data off the partition first. Right now, the current attempt is to do e2fsck on it, to replace the superblock, but it says that /dev/sda is mounted or opened by another program, even though I'm on the LiveCD.

---

### Post by eyefragment on 2008-10-20
Apologies if you've already tried the following fixes, but I was getting the same error recently.

1)  If you are getting grub error 17 before you get to the "choose OS" part of grub, try resetting grub as per the instructions here:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

2)  If you are getting error 17 after you choose an OS (Can't mount the correct disk or something), then your disk topology has recently changed.  To fix this, you can probably press "e" to edit grub's info, and  change hd(0,x) to hd(0,y) where y is the correct partition.

Hope this helps.

---

### Post by jerome1232 on 2008-10-20
Just to check that it's in fact not mounted, I'm assuming that it's /dev/sda1, adjust accordingly.

```
sudo umount /dev/sda1
```

---

### Post by Yoshidude on 2008-10-20
I don't multi-boot, so I never have to choose the OS. When I try to do 
```
find /boot/grub/stage1
```
in grub, it tells me that it can't find that. I think it's Error 15, but I can double-check if it would be helpful.
I found another fix for that, which is what I mentioned in my first post, but that didn't work, because the filesystem doesn't seem to be ext3 anymore.

And when I try to unmount /dev/sda1, it says that it isn't found in mtab.

---

### Post by caljohnsmith on 2008-10-20
How about posting:
```
sudo fdisk -lu
```
So we can get a better idea of your HDD setup.

---

### Post by Yoshidude on 2008-10-20
What I get from fdisk:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d702ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   228428234   114214086   83  Linux
/dev/sda2       228428235   234436544     3004155    5  Extended
/dev/sda5       228428298   234436544     3004123+  82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-10-20
OK, so you boot your Live CD, and you're saying you get an mtab error when you do the following:
```
sudo umount /dev/sda1
```
And does the following show sda1 is mounted:
```
mount | grep sda1
```
If sda1 isn't mounted, can you try again:
```
sudo fsck -y /dev/sda1
```
If it complains about bad superblocks, you could try this method of using a backup superblock:

[http://ubuntuforums.org/showpost.php?p=5806996](http://ubuntuforums.org/showpost.php?p=5806996)

And replace the "sda5" with "sda1". Also, what happened to your computer or Ubuntu that led up to getting the Grub error 17?

---

### Post by Yoshidude on 2008-10-20
Because having the | gives me nothing, I'm assuming that your second statement should say

```
mount grep sda1
```
This tells me that the mount point sda1 does not exist. So I try the fsck and it complains about a bad superblock. When I go over to your link, and try to do dumpe2fs, it complains about a bad magic number in the superblock.

As for what happened, I'm not sure exactly. My computer had been having various weird problems, like programs hanging randomly, some taking ages to open, etc. Then I realized that I could hear my hard drive making a repetitive sound, so I used supermontools, which showed a bad LBA. So I tried to use their bad block HOWTO at [http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html) to fix it. Stupid me didn't make a backup because I was lazy and this is the result.

---

### Post by Yoshidude on 2008-10-21
I'm just going to format, thanks for trying to help. I do appreciate it.

---

