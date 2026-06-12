---
title: "ubuntu not found"
date: 2008-11-06
forum: General Help
---

### Post by SpikeyMike on 2008-11-06
I have a problem, I restored the grub menu from a live cd, I installed it on the drive where ubuntu is installed. The thing is now ubuntu won't start, I see the splash screen and then after a couple of minutes I see:

[COLOR="Red"]busybox v1.1.3

..................

(initramfs)[/COLOR]

and cannot go any further, I tried booting ubuntu recovery mode but then I see the following:

[COLOR="Red"]
check root= bootarg cat /proc/cmdline
or missing modules devices: cat /proc/modules ls/dev
ALERT! /dev/disk/ by-uuid/06bde937-1412-421d-a18f-867e43559455 does not exist. Dropping to a shell!

busybox v1.1.3

.................

(initramfs)[/COLOR]

does this mean it cannot find my ubuntu installation? any help appreciated

Spikey

---

### Post by meierfra. on 2008-11-07
Maybe one of the  UUIDs in menu.lst or /etc/fstab is wrong.  Post the files "menu.lst" and "/etc/fstab" from the  Ubuntu partition and also post the output of

```
sudo fdisk -lu
sudo blkid 
```

---

### Post by SpikeyMike on 2008-11-08
> **meierfra. said:**
> Maybe one of the  UUIDs in menu.lst or /etc/fstab is wrong.  Post the files "menu.lst" and "/etc/fstab" from the  Ubuntu partition and also post the output of

```
sudo fdisk -lu
sudo blkid 
```

thanks for your reply, to do that I think I need to boot from a live cd and mount the hard drive? i'm not exactly sure how I mount the drive, can you advise me?

Spikey

---

### Post by meierfra. on 2008-11-08
> i'm not exactly sure how I mount the drive, can you advise me?

Boot from the LiveCD, open a terminal (Application->Accessories->Terminal) and type

```
sudo fdisk -lu
sudo blkid
```

Looking at the output you should be able to figure out the device name of your Ubuntu partition,  something of the form /dev/sdXY, where X is a letter  and Y a number. Like /dev/sda2 or /dev/sdb1.

Then mount your Ubuntu Partition via:

```
sudo mount /dev/sdXY   /mnt
```

and open "fstab" and "menu.lst" via
```
gksudo gedit /mnt/etc/fstab

gksudo gedit /mnt/boot/grub/menu.lst
```

---

### Post by SpikeyMike on 2008-11-08
here is the output from sudo fdisk -lu and sudo blkid, when I try to open fstab and menu.lst I get an error message saying no such file or directory then it opens a blank page :confused:


[COLOR="Red"]
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a5e8f56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104856254    52428096    7  HPFS/NTFS
/dev/sda2       572492340   586067264     6787462+   c  W95 FAT32 (LBA)
/dev/sda3       104856255   572492339   233818042+   f  W95 Ext'd (LBA)
/dev/sda5       104856318   572492339   233818011    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000baf32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   146801969    73400953+  83  Linux
/dev/sdb2       153774180   160071659     3148740   82  Linux swap / Solaris

Disk /dev/sdc: 2041 MB, 2041577472 bytes
61 heads, 60 sectors/track, 1089 cylinders, total 3987456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             240     3987455     1993608    6  FAT16
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="54F06DC5F06DAE44" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="3E1F-178E" TYPE="vfat" 
/dev/sda5: UUID="140DA8BB87390D11" LABEL="Media 1" TYPE="ntfs" 
/dev/sdb1: LABEL="Ubuntu" UUID="06bde937-1412-421d-a18f-867e43559455" TYPE="ext2" 
/dev/sdb2: TYPE="swap" UUID="6e63b9f2-948f-4ba9-8912-47722d70314d" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="E0FD-1813" TYPE="vfat" [/COLOR]

---

### Post by meierfra. on 2008-11-08
> when I try to open fstab and menu.lst I get an error message saying no such file or directory then it opens a blank page

Try this

```
sudo  mount -t ext3  /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

Copy  the whole screen and post it here, so that I can see the output and/or any error messsages (click on the "#" symbol and place it inside the code tags, )

---

### Post by SpikeyMike on 2008-11-08
> **meierfra. said:**
> Try this

```
sudo  mount -t ext3  /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

Copy  the whole screen and post it here, so that I can see the output and/or any error messsages (click on the "#" symbol and place it inside the code tags, )

here is the output when I try to mount the drive:

[COLOR="Red"]ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ [/COLOR]

---

### Post by meierfra. on 2008-11-08
> mount: wrong fs type, bad option, bad superblock on /dev/sdb1,

Seems  that something is wrong with the  Ubuntu filesystem (or with your  Ubuntu drive) Anything which could have caused this? Power outage?  Forced shutdown? How old is the hard drive?

Try a file system check

```
sudo e2fsck  -fy /dev/sdb1
```


If e2fsck fails to run:

Go to "System>Administration->Software Sorces" and enable all the repositories in the "ubuntu software" tab.

```


sudo apt-get install testdisk

sudo testdisk /dev/sdb
```

Choose "proceed", "intel" and "advanced"

Select your ubuntu partition (sdb1) and then "Superblock"


This should list all superblocks:

superblock 0, blocksize=4096
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096


Use these numbers with "e2fsck":


```
sudo e2fsck -b  32768 -fy /dev/sdb1
```

If that fails:

```
sudo e2fsck -b  98304 -fy /dev/sdb1
```

Try as many as you like.

---

### Post by SpikeyMike on 2008-11-08
i tried that on all the superblocks it listed and it corrected some errors:

[COLOR="Red"]Free inodes count wrong for group #544 (16352, counted=16316).
Fix? yes[/COLOR]

it found alot of these for each superblock. I tried mounting the disk again after this had finished but got the same error. not sure what happened to the disk, it was working fine until I reinstalled grub....

Spikey

---

### Post by meierfra. on 2008-11-08
> it found alot of these for each superblock


I suggest  to keep running "e2fsck" until it does  not return any errors. Does e2fsck run without the "-b ..." option?  (It shouldn't matter which superblock you use, as long as e2fsck is actually running)

Did you try

```
sudo  mount -t ext3  /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

again?


> until I reinstalled grub..
Why did you reinstall grub?

---

### Post by SpikeyMike on 2008-11-09
> **meierfra. said:**
> I suggest  to keep running "e2fsck" until it does  not return any errors. Does e2fsck run without the "-b ..." option?  (It shouldn't matter which superblock you use, as long as e2fsck is actually running)

Did you try

```
sudo  mount -t ext3  /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

again?


Why did you reinstall grub?

Thanks for your assistance, I found out why it wouldn't mount, the disk is ext2 not ext3, I also managed to get it to boot, I swapped the sata cables for the two drives and it worked, seemed the problem was that the drive was set as hd0,0 in menu.lst but was drive sdb1, now it is sda1. There is still a problem though, I had to replace the UUID of the drive in menu.lst with /dev/sda1, for some reason it won't boot with the UUID, I checked this using sudo blkid  and the UUID was correct but for some reason it doesn't work, any ideas about this?

The reason I reinstalled grub was because I was having trouble getting windows to boot when I added a third hard drive, I thought it might have been something to do with the grub menu

Spikey

---

### Post by meierfra. on 2008-11-09
> I had to replace the UUID of the drive in menu.lst with /dev/sda1, for some reason it won't boot with the UUID, I checked this using sudo blkid and the UUID was correct but for some reason it doesn't work, any ideas about this?

No idea.

What error messages where you getting? 

 If you want to pursue the issue post "sudo fdisk -lu", "sudo blkid", "menu.lst" and "fstab"

---

### Post by SpikeyMike on 2008-11-09
> **meierfra. said:**
> No idea.

What error messages where you getting? 

 If you want to pursue the issue post "sudo fdisk -lu", "sudo blkid", "menu.lst" and "fstab"

here is the output of sudo fdsik -lu:

[COLOR="Red"]mikey@Ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000baf32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   146801969    73400953+  83  Linux
/dev/sda2       153774180   160071659     3148740   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a5e8f56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   104856254    52428096    7  HPFS/NTFS
/dev/sdb2       572492340   586067264     6787462+   c  W95 FAT32 (LBA)
/dev/sdb3       104856255   572492339   233818042+   f  W95 Ext'd (LBA)
/dev/sdb5       104856318   572492339   233818011    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 163.9 GB, 163928604160 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4a4b4a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16065   320159384   160071660    f  W95 Ext'd (LBA)
/dev/sdc5           16128   320159384   160071628+   7  HPFS/NTFS[/COLOR]

here is the output of blkid:

[COLOR="Red"]mikey@Ubuntu:~$ sudo blkid
/dev/sdb1: UUID="54F06DC5F06DAE44" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sdb5: UUID="140DA8BB87390D11" TYPE="ntfs" LABEL="Media 1" 
/dev/sda1: LABEL="Ubuntu" UUID="06bde937-1412-421d-a18f-867e43559455" TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="6e63b9f2-948f-4ba9-8912-47722d70314d" 
/dev/sdb2: LABEL="HP_RECOVERY" UUID="3E1F-178E" TYPE="vfat" 
/dev/sdc5: UUID="025A46F65A46E64F" TYPE="ntfs" 
[/COLOR]

here is the output of menu.lst:

[COLOR="Red"]title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro single
#initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Centre
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
[/COLOR]

here is the output of fstab:

[COLOR="Red"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=06bde937-1412-421d-a18f-867e43559455 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=6e63b9f2-948f-4ba9-8912-47722d70314d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0[/COLOR]

---

### Post by meierfra. on 2008-11-09
Strange.  I don't see anything wrong. 
What exactly happened when you tried booting with the "root=UUID=..." in the kernel line? Any error messages?
Are you able to boot into recovery mode? (Its still using  the UUID).

Just curios: Why are you using ext2 instead of ext3?

---

### Post by TeXtonyx on 2008-11-09
I got that error message yesterday. I had tried to update 8.04 to
8.10 over the internet and the computer rebooted during this. I
decided to return to 8.04 because I have the cd. The first time 
Ubuntu booted after the reinstallation of 8.04 I got your error.

Fat32 is on the first partition of my second drive and Ubuntu is
on the second partition. The Fat32 partition, which has no OS, just
data, had been marked active with an asterisk * , sdb1 was active.

The only file I found in /boot/grub/ I think was dev.map, something
like that. There were no stage1 files (I install to /boot not MBR),
none of the other grub stuff, and no menu.lst!

So I used gparted I think to delete the Ubuntu partition. The swap
partition wouldn't delete. Then I used as usual,  intall Ubuntu to
'largest free space (guided)' again. 

This time at the end, the Ubuntu partition, sdb2 was marked active
and I had a populated /boot/grub/ directory with all the files.
I posted because the correct *active* partition might be relevant.
This error is an interesting problem, first time it happened to me.
Now I have two swap partitions :-)

After reading more carefully. At one time I had Ubuntu on both drive 0
sda5, and I cloned it to drive 1, sdb5 at the time. Now Ubuntu on hd1
appeared to boot. But when I deleted Ubuntu on hd0, Ubuntu on hd1 would
no longer boot. It seemed that the problem was that the cloned Ubuntu/hd1
had the same UUID as the Ubuntu on drive hd0.

I followed the instructions to assign a new UUID and I think I added it 
to fstab also. Well, it didn't work. There must be some other step involved
in changing the UUID. I couldn't figure it out, so I wound up reinstalling
Ubuntu once again which lost the customization, which is why I had cloned
the partition in the first place. I'll try to find a Howto and post it.

---

### Post by TeXtonyx on 2008-11-09
I remembered where I got stuck before with changing the UUID, it was
with tune2fs. Did you have any problem with tune2fs and ext2? 
--------------
Howto

"A combo of using uuidgen to generate the identifier and tune2fs to 
assign that uuid to a particular filesystem will do the trick."

--------------------------------------------

[http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html](http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html)

Right, found the answer after reading 5 times the man pages
and a bit of imagination

uuidgen
tune2fs /dev/hdaX -U numbergeneratedbyuuidgen
verification with
vol_id /dev/hdaX

one can use xargs or a variable and ; to make that a one liner

uuidgen | xargs tune2fs /dev/hdaX -U ; vol_id /dev/hdaX

-----------------------------------------------
or
   1. $ uuidgen  
   2. $ tune2fs /dev/hdaX -U numbergeneratedbyuuidgen  
   3. $ vol_id /dev/hdaX  

------------------------------------------------------

[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

Converting from Ext2 to Ext3

The conversion procedure is simple enough. Imagine /dev/hda10 mounted as /test &#8211; 
the procedure would be as follows:

    * Log in as root
    * Make sure /etc/fstab has /dev/hda10 mounted to /test as ext2, read write
    * umount /dev/hda10
          o If you can't unmount it, then remount it read only (mount -o remount,ro /dev/hda10)
    * tune2fs -j /dev/hda10
    * Edit /etc/fstab, and for /dev/hda10, change ext2 to ext3
    * mount /dev/hda10
    * /sbin/shutdown -h now
    * mount | grep /dev/hda10
          o If it's not shown as ext3, reboot, if still not, troubleshoot
          o Otherwise, you're done.

A few explanations are in order. The tunefs command creates the journal file, 
which is kept in a special inode on the device (by default). You then must 
change the /etc/fstab entry to reflect it's a journalling filesystem, and then 
mount it.

-------------------------------------------------------
[http://www.oreillynet.com/linux/cmd/cmd.csp?path=t/tune2fs](http://www.oreillynet.com/linux/cmd/cmd.csp?path=t/tune2fs)

---

### Post by SpikeyMike on 2008-11-10
> **meierfra. said:**
> Strange.  I don't see anything wrong. 
What exactly happened when you tried booting with the "root=UUID=..." in the kernel line? Any error messages?
Are you able to boot into recovery mode? (Its still using  the UUID).

Just curios: Why are you using ext2 instead of ext3?

when i tried to boot with the uuid I got the splash screen then after about 3 minutes a message saying it couldn't find the volume with UUID=blablabla and that it was dropping to a kernel, then I got busybox, hope this helps....

Spikey

---

### Post by meierfra. on 2008-11-10
Maybe the UUID in the kernel line somehow got messed up (although that's seems unlikely since all the other UUID on menu.lst are correct).

So I suggest to try again with the UUID:

```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic with UUID
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro single
initrd /boot/initrd.img-2.6.24-19-generic

```
so add an extra item using the UUID (then you still will  be  able to boot into Ubuntu, even if the UUID item fails.)

If booting  with UUID still fails, you should change the line

# kopt=root=UUID=6bde937-1412-421d-a18f-867e43559455 ro

in menu.lst to

# kopt=root=/dev/sda1 ro

otherwise you will run into problems after the next kernel update.


Did you try booting to recovery mode?

---

### Post by SpikeyMike on 2008-11-13
> **meierfra. said:**
> Maybe the UUID in the kernel line somehow got messed up (although that's seems unlikely since all the other UUID on menu.lst are correct).

So I suggest to try again with the UUID:

```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic with UUID
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=06bde937-1412-421d-a18f-867e43559455 ro single
initrd /boot/initrd.img-2.6.24-19-generic

```
so add an extra item using the UUID (then you still will  be  able to boot into Ubuntu, even if the UUID item fails.)

If booting  with UUID still fails, you should change the line

# kopt=root=UUID=6bde937-1412-421d-a18f-867e43559455 ro

in menu.lst to

# kopt=root=/dev/sda1 ro

otherwise you will run into problems after the next kernel update.


Did you try booting to recovery mode?

sorry for my slow reaction, now ubuntu won't boot at all, I also tried recovery mode but that doesn't work either, when I boot ubuntu I see the splash screen for a few seconds then it goes straight to busybox, I am still using /dev/sda1 in menu.lst so i'm really not sure whats going on here :confused::confused::confused:

---

### Post by meierfra. on 2008-11-13
I'm not sure what is going on. A few things to try:

1)   Make sure you hard drive is not failing. This link contains instruction how to use "smartmontools" to check on your harddrive:

[http://ubuntuforums.org/showthread.php?p=6088520#29]("http://ubuntuforums.org/showthread.php?p=6088520#29")


2)  Check out your cables. Make sure they are in good shape and not loose.

3)  Run "e2fsck" again.

---

