---
title: "Grub Error 22 on boot"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by mreude on 2008-12-09
I have just installed Ubuntu 8.10 with GRUB loader. When I boot to HDD I get the following information:

Grub 1.5 Loading...

ERROR 22

I have been all over the forums, but cannot find the information to get GRUB to load properly.

Here is the information I have aquired so far.

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcdb8cdb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99c0d4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   487412099   243706018+   7  HPFS/NTFS
/dev/sdb2       487412100   976768064   244677982+   5  Extended
/dev/sdb5       487412163   970759754   241673796   83  Linux
/dev/sdb6       970759818   976768064     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08e00c86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   120085874    60042906    7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75eab9f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/sde: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders, total 196608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93e2014e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde4   *          32      196607       98288    6  FAT16

Disk /dev/sdk: 4009 MB, 4009230336 bytes
16 heads, 32 sectors/track, 15294 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe12de12d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *          32     7830527     3915248    b  W95 FAT32

> ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda
eb48
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdb
eb48
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdc
eb48
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdd
eb48
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sde
eb48
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdk
eb48

They all say eb48 because I've tried to install GRUB on all of my drives.

> ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0481
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
04ff
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdc
0481
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdd
0481
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sde
0481
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdk
0481

Ubuntu 8.10 is installed on sdb5. And GRUB says that it is installed on hd1,4 when I do the following:

> sudo grub
find /boot/grub/stage1

---

### Post by caljohnsmith on 2008-12-09
OK, according to the output of the commands you posted, you have Grub installed to the MBR of all six of your drives. The good news though is that the Grub you have installed to your Ubuntu sdb drive points to the correct drive/partition for its boot files, namely sdb5. That means if you can change your BIOS to boot your sdb drive on start up, you should at least get the Grub menu, and most likely you'll be able to boot into Ubuntu just fine. How about giving that a shot and let me know how it goes. :)

---

### Post by mreude on 2008-12-10
Ok, by changing my HDD boot order I was able to get GRUB to load. I can select Ubuntu to get it to load and it does. But I cannot get to my Windows XP Home installation. If I select "Windows XP Home Edition" from the list it displays "Starting up...." on the screen and stops. If I select "Windows XP Home Edition (loader)" it displays "Starting up.... | GRUB" and stops.

Any thoughts?

---

### Post by caljohnsmith on 2008-12-10
So which drive is Windows on? How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace whatever entry you have for Windows with the following entries:
```

title       Windows XP (hd0)
root       (hd0,0)
chainloader +1

title       Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title       Windows XP (hd4)
root       (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
Reboot, try each entry above from the Grub menu, and one should work if you don't have any issues with Windows. If none of them work, let me know exactly what happens when you try each one from the Grub menu.

---

### Post by mreude on 2008-12-30
Ok, I just added the Windows XP entries from the last post. I ran:

> sudo fdisk -lu

I received the following results:

> Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08e00c86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   120085874    60042906    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcdb8cdb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99c0d4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   487412099   243706018+   7  HPFS/NTFS
/dev/sdc2       487412100   976768064   244677982+   5  Extended
/dev/sdc5       487412163   970759754   241673796   83  Linux
/dev/sdc6       970759818   976768064     3004123+  82  Linux swap / Solaris

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75eab9f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/sde: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders, total 196608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93e2014e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde4   *          32      196607       98288    6  FAT16

Disk /dev/sdj: 4009 MB, 4009230336 bytes
16 heads, 32 sectors/track, 15294 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe12de12d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *          32     7830527     3915248    b  W95 FAT32


I believe the Windows partition is on sdb, but I'm not entirely sure.

Standby for another post with results from the Windows XP entries.

---

### Post by mreude on 2008-12-30
Here are the results from the Windows XP entries:

Windows XP (hd0)
> Starting up ...
CTRL + ALT + DEL = reboot

Windows XP (hd1)
> Starting up ...
GRUB Loading stage2...
CTRL + ALT + DEL = reboot

Windows XP (hd2)
> Starting up ...
GRUB <blinking cursor
CTRL + ALT + DEL = no reboot

Windows XP (hd3)
> Error 22: No such partition

Press any key to continue...
Pressing a key returns to GRUB

Windows XP (hd4)
> Error 21: Selected disk does not exist

Press any key to continue...
Pressing a key returns to GRUB

GRUB is installed all all drives. Should I maybe set it to boot to hd#,1 instead of hd#,0)?

---

### Post by caljohnsmith on 2008-12-30
Based on the results you posted, I think the (hd0) entry might be correct. Having it hang on "starting up" though sometimes can be caused by problems with the Windows boot sector, so I think we should check it to make sure that's not a problem. To check the Windows boot sector, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk claims the boot sectors are identical, please let me know and post the screen where it says that.

Also, if testdisk doesn't solve the booting problem with Windows, next do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by tad1073 on 2008-12-30
This link is all you need.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)[URL="http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1335581"]
[/URL]

---

