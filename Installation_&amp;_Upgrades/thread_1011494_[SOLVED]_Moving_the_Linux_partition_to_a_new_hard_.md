---
title: "[SOLVED] Moving the Linux partition to a new hard drive"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by cyran on 2008-12-14
I'm trying to transfer my Ubuntu installation onto a new laptop, which already has Windows installed on it [which I'd like to keep there]. Shrinking the Windows partition, then copying the Ubuntu partitions onto the new drive, was easy, with GParted's Copy/Paste, and a hard drive enclosure[containing my old drive]. But now I'm not sure how to boot into the Ubuntu partition or install & reconfigure GRUB for dual-booting.

So, does anyone else know?

---

### Post by caljohnsmith on 2008-12-14
How about first booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And please identify all your partitions. We can work from there if you want.

---

### Post by cyran on 2008-12-15
Thanks. Here:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa07b3e3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   214435619   107217778+   7  HPFS/NTFS
/dev/sda2       214435620   214965764      265072+  83  Linux
/dev/sda3       214965765   312576704    48805470    5  Extended
/dev/sda5       214965828   256895414    20964793+  83  Linux
/dev/sda6       308335608   312576704     2120548+  82  Linux swap / Solaris


```
sda1 is Windows, sda2 is /boot, sda5 is the rest of Ubuntu in /, then there's a few gigs of empty space, and sda6 is swap.

---

### Post by joff13 on 2008-12-15
> **cyran said:**
> Thanks. Here:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa07b3e3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   214435619   107217778+   7  HPFS/NTFS
/dev/sda2       214435620   214965764      265072+  83  Linux
/dev/sda3       214965765   312576704    48805470    5  Extended
/dev/sda5       214965828   256895414    20964793+  83  Linux
/dev/sda6       308335608   312576704     2120548+  82  Linux swap / Solaris


```
sda1 is Windows, sda2 is /boot, sda5 is the rest of Ubuntu in /, then there's a few gigs of empty space, and sda6 is swap.

edit /boot/grub/menu.lst edding something like:

```

title ubuntu
kernel (hd0,1)/boot/vmlinuz root=/dev/sda5 
initrd (hd0,1)/boot/initrd.gz

```

for windows ther should be an example at the end of the file to uncomment 

But when you install grub using ubuntu, the file should be filled out correctly by the installer

---

### Post by caljohnsmith on 2008-12-15
OK, how about doing the following, and please post the output of all the commands:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
sudo mkdir /mnt/sda2 /mnt/sda5
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda5 /mnt/sda5
cat /mnt/sda5/etc/fstab
cat /mnt/sda5/etc/initramfs-tools/conf.d/resume
```
From the above "cat" commands, check that the swap partition UUID agrees in both the "resume" file and the "fstab" file, and if it does, then copy/paste that swap UUID into:
```
sudo mkswap -U "[COLOR="Blue"]<Swap UUID>[/COLOR]" /dev/sda6
```
Then find the original UUID of the Ubuntu root partition by doing:
```
grep " / " /mnt/sda5/etc/fstab
```
Then copy/paste that UUID into:
```
sudo tune2fs -U "[COLOR="Blue"]<Ubuntu partition UUID>[/COLOR]" /dev/sda5
```
Next do the same for your /boot partition:
```
grep " /boot" /mnt/sda5/etc/fstab
```
Copy/paste that UUID into:
```
sudo tune2fs -U "[COLOR="Blue"]<Boot partition UUID>[/COLOR]" /dev/sda2
```
Lastly open your menu.lst:
```
gksudo gedit /mnt/sda2/grub/menu.lst
```
And check that each Ubuntu entry looks similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
[COLOR="Blue"]root            (hd0,1)[/COLOR]
kernel		/vmlinuz-2.6.27-9-generic root=UUID=[COLOR="Blue"]<UUID of Ubuntu sda5 partition>[/COLOR] ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet
```
Note there is no "/boot" directory in front of the vmlinuz and initrd files in the above entry since you have a boot partition. After doing everything above, reboot, and let me know exactly what happens. We can work from there.

---

### Post by cyran on 2008-12-16
Thanks, that fixed everything; I'm dual-booting now.

Just some notes on what happened:

"vol_id -u /dev/sda2" and "vol_id -u /dev/sda5" showed that the UUID's of those two partitions hadn't changed when copying onto the new disk, so the tune2fs steps didn't do or change anything.

The swap partition's UUID *did* seem to be different now (possibly because I resized it to be bigger, which may have simply created a new one from scratch), but my version of "mkswap" didn't offer the "-U" argument. (Or the lowercase "-u" argument either.) I was using the [System Rescue CD]("http://www.sysresccd.org/Main_Page") version 1.0.3 (made into a bootable flash drive with syslinux). So I just edited fstab and the 'initramfs-tools/conf.d/resume' files instead.

I made a slight change and installed grub to the boot partition (hd0,1) instead of the MBR (hd0), executed "dd if=/dev/sda2 of=grub.bin count=1 bs=512", copied grub.bin into the Windows filesystem, and added it to Windows XP's boot.ini.

Thanks again!

---

