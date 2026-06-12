---
title: "NTLDR is missing - Both OSs boot"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by Kakistos on 2008-12-09
I recently installed Ubuntu and began getting the following error message.

"NTLDR is missing
Press any key to restart"

When I press any key I get to the grub boot menu.  Both Ubuntu and Windows boot up fine.  It's just an annoying error message.  

I've tried the Windows based repair.  Booting up with the XP cd.  Getting to the repair console and copying the files ntldr and ndetect to the Windows root directory.

Any ideas?  I've searched these forums and googled the problem with no luck.

Cheers

Chris

---

### Post by mk1w86 on 2008-12-09
Try booting the Ubuntu live cd and running 

```
sudo grub-install
```

to reinstall grub to the Master Boot Record.


You can also use the Super Grub Disk to reinstall grub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by pietjanjaap on 2008-12-09
Do you have more then 1 hd?
Are booting from the disk were grub is installed?

---

### Post by Pumalite on 2008-12-09
Maybe this will help you:
[http://ubuntuforums.org/showthread.php?t=813628&highlight=meierfra](http://ubuntuforums.org/showthread.php?t=813628&highlight=meierfra)

---

### Post by caljohnsmith on 2008-12-09
If you have more than one NTFS partition, it could be you are getting the "NTLDR missing" error because Grub is trying to boot the wrong NTFS partition. How about first opening a terminal (Applications > Accessories > Terminal) and post the output of:
```

cat /boot/grub/menu.lst
sudo fdisk -lu
```
And please identify which is the Windows partition. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
That will help clarify your setup and how Grub is booting Windows.

---

### Post by Pumalite on 2008-12-09
You can also use Super Grub and if you can boot Windows; you'll know your system is intact

---

### Post by dragos_iliescu_2005 on 2008-12-09
I had in the past the same problem. At that time, my Windows resides on disk D, but the masterboot was the disk C. These files, needed by Windows to boot, must to be located on the root location (disk C).

---

### Post by Kakistos on 2008-12-10
> **caljohnsmith said:**
> If you have more than one NTFS partition, it could be you are getting the "NTLDR missing" error because Grub is trying to boot the wrong NTFS partition. How about first opening a terminal (Applications > Accessories > Terminal) and post the output of:
```

cat /boot/grub/menu.lst
sudo fdisk -lu
```
And please identify which is the Windows partition. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
That will help clarify your setup and how Grub is booting Windows.

Here's all the info you wanted.

cat /boot/grub/menu.lst

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-16-generic root=UUID=f87b73de-c5ac-4905-955b-74e5668b2bcc ro quiet splash
initrd          /boot/initrd.img-2.6.22-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-16-generic root=UUID=f87b73de-c5ac-4905-955b-74e5668b2bcc ro single
initrd          /boot/initrd.img-2.6.22-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title XP
rootnoverify (hd0,0)
chainloader +1

sudo fdisk -lu

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22a6e1e1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    34812854    17406396    7  HPFS/NTFS	//This is the windows partition
/dev/hda2        34812855    36772784      979965   82  Linux swap / Solaris
/dev/hda3        36772785    80405324    21816270   83  Linux

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5442f682

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   390716864   195358401    c  W95 FAT32 (LBA)		//This is just used for storing data


sudo xxd  -l  2 -p /dev/hda
eb48
sudo xxd  -l  2 -p /dev/hdb
33c0

sudo xxd -s 1049 -l 2 -p /dev/hda
02ff

Thanks

Chris

---

### Post by caljohnsmith on 2008-12-10
OK, that's great, the output you posted clears up a lot of the ambiguity; your Windows entry in Grub is just fine, and since your hdb1 partition is marked as bootable, probably what happened is Windows put its boot files on your hdb1 drive. Therefore, when you boot Windows from your hda drive, Windows complains that "ntldr is missing", because "ntldr" is most likely in your hdb1 partition. How about posting the output of:
```
sudo mkdir /mnt/hda1 /mnt/hdb1
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hdb1 /mnt/hdb1
ls -l /mnt/hda1 /mnt/hdb1
cat /mnt/hdb1/boot.ini
```
And we can work from there. :)

---

### Post by Kakistos on 2008-12-10
> **caljohnsmith said:**
> OK, that's great, the output you posted clears up a lot of the ambiguity; your Windows entry in Grub is just fine, and since your hdb1 partition is marked as bootable, probably what happened is Windows put its boot files on your hdb1 drive. Therefore, when you boot Windows from your hda drive, Windows complains that "ntldr is missing", because "ntldr" is most likely in your hdb1 partition. How about posting the output of:
```
sudo mkdir /mnt/hda1 /mnt/hdb1
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hdb1 /mnt/hdb1
ls -l /mnt/hda1 /mnt/hdb1
cat /mnt/hdb1/boot.ini
```
And we can work from there. :)


Here you go.  I've got both drives mounting in /media already.  

ls -l /media/hda1/ /media/hdb1
/media/hda1/:
total 2095857
drwxrwxrwx 1 root root          0 2006-07-14 15:41 ATI
-rwxrwxrwx 1 root root          0 2006-07-14 10:19 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        173 2008-06-05 19:18 boot.ini
-rwxrwxrwx 2 root root        211 2006-11-28 23:56 boot.ini.comodofirewall
drwxrwxrwx 1 root root          0 2008-09-08 20:38 cabs
drwxrwxrwx 1 root root       8192 2008-11-30 11:26 Config.Msi
-rwxrwxrwx 1 root root          0 2006-07-14 10:19 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-06-06 16:35 Documents and Settings
-rwxrwxrwx 1 root root          0 2006-07-14 10:19 IO.SYS
-rwxrwxrwx 1 root root          0 2006-07-14 10:19 MSDOS.SYS
drwxrwxrwx 1 root root       4096 2008-06-06 16:38 NBGuide
-rwxrwxrwx 1 root root      47580 2002-09-16 06:50 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2004-08-04 13:00 ntldr
-rwxrwxrwx 1 root root     233632 2002-09-16 06:50 NTLDR
drwxrwxrwx 1 root root          0 2008-07-02 16:00 OEMSettings
-rwxrwxrwx 1 root root 2145386496 2008-12-08 15:09 pagefile.sys
drwxrwxrwx 1 root root      16384 2008-11-25 12:10 Program Files
drwxrwxrwx 1 root root          0 2006-07-27 11:40 RECYCLER
drwxrwxrwx 1 root root          0 2008-09-08 20:38 Swsetup
drwxrwxrwx 1 root root       4096 2008-11-25 12:19 System Volume Information
-rwxrwxrwx 2 root root        712 2008-10-12 18:10 UBSoftUpdate.log
drwxrwxrwx 1 root root     126976 2008-12-07 17:04 WINDOWS
drwxrwxrwx 1 root root      61440 2007-11-08 13:21 WUTemp

/media/hdb1:
total 72
drwxrwx---   4 root plugdev  4096 2008-07-04 14:25 Canada
drwxrwx---  16 root plugdev  4096 2008-11-22 11:16 Chris
drwxrwx---  21 root plugdev  8192 2008-11-05 22:10 Jenny
drwxrwx---   6 root plugdev  8192 2008-11-09 13:15 Movies
drwxrwx--- 161 root plugdev 16384 2008-11-19 21:58 My Music
drwxrwx---  58 root plugdev 12288 2008-11-14 20:48 Pictures
drwxrwx---   2 root plugdev  4096 2008-09-01 23:07 Recycled
drwxrwx---  15 root plugdev  4096 2008-07-23 10:50 Setup
drwxrwx---   2 root plugdev  8192 2008-11-16 11:57 Sheetmusic
drwxrwx---   3 root plugdev  4096 2008-10-20 15:18 System Volume Information

As boot.ini isn't in hdb1, I'll post the output of boot.ini in hda1.

cat /media/hda1/boot.ini
[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect

Cheers

Chris

---

### Post by caljohnsmith on 2008-12-10
OK, I think I misunderstood your original "NTLDR missing" error; when you turn on your computer, what exactly happens? Do you immediately get the "NTLDR missing" error, and then when you press a key you get the Grub menu and can boot Ubuntu/Windows? If that's the case, it might be that you have your BIOS set to boot your hdb drive before the hda drive. How about checking your BIOS boot order see if that is the case. Let me know how that goes.

---

### Post by Kakistos on 2008-12-10
That has solved the problem. Bios was booting the wrong hard drive.  Thanks so much.  You've been excellent. :guitar:

Chris

---

### Post by caljohnsmith on 2008-12-10
Glad to hear that solved the problem; cheers and have fun with your OSes. :)

---

