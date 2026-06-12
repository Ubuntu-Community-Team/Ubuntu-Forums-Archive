---
title: "Grub bootloader gone after Windows 7 installed"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by The Patriot on 2009-02-15
I had Window XP and Ubuntu 9.04 Aplha, I was happy with my OS installed until I decided to install Window 7 Beta and it messed up my Grub bootloader and now I cannot boot to Ubuntu but the partition is still there. Can someone help me get my bootloader back. I try everything in the internet and whatever I do to get Grub back I get Error 15. Btw Window XP and Window 7 just boots fine with Windows own bootloader. Please don't tell me to reformat Ubuntu. It had memories there that I do not want to lose and all those eye candy that i installed. Thank you.

P.S. I have tried Super Grub disk but to no avail.
  ```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hdc
 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g defaults,force 0 0

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda4': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda4 sda4 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda4': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda4 sda4 ntfs-3g defaults,force 0 0

=========================== Drive/Partition Info: =============================

Drive hdc: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 729 MB, 729608192 bytes
255 heads, 63 sectors/track, 22 cylinders, total 356254 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5147e9d5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   162,079,784   162,079,722   7 HPFS/NTFS
/dev/sda2         226,387,980   234,436,544     8,048,565  1c Hidden W95 FAT32 (LBA)
/dev/sda3         193,406,535   226,387,979    32,981,445   5 Extended
/dev/sda5         224,910,063   226,387,979     1,477,917  82 Linux swap / Solaris
/dev/sda6         193,406,661   224,909,999    31,503,339  83 Linux
/dev/sda4         162,079,785   193,406,534    31,326,750   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FA30CC8130CC45FB" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda2: LABEL="HDDRECOVERY" UUID="9433-FC77" TYPE="vfat" 
/dev/sda4: UUID="2A280EA7280E71DD" LABEL="Windows 7 Alpha" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="fa31930e-24ef-4b96-96f8-9b5c99d70bb2" 
/dev/sda6: UUID="0fab507d-7637-42aa-94cf-de9d9b69dcef" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda2: device is busy
umount: /tmp/BootInfo/sda2: device is busy
cat: /tmp/BootInfo/Log1: No such file or directory
```

---

### Post by x33a on 2009-02-15
you'll have to fix grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by The Patriot on 2009-02-15
I already went though that.
find /boot/grub/stage1        Error 15
find /grub/stage1       still Error 15

that what stopping me right there.

---

### Post by The Patriot on 2009-02-15
Ok I found out that my Ubuntu system is somewhere located in (hd0,5)  Ok I typed setup hd0,5 and return with: 
"checking if file exist.../boot/grub/menu.lst...no"
"checking if file exist.../grub/menu.lst...no"

Please help me, I am at lost.

---

### Post by x33a on 2009-02-16
see if you can access the jaunty partition from the live cd.

if you can access the drive, then post the output of
```
df -h
cat /boot/grub/menu.lst
cat /etc/fstab
sudo fdisk -l
```

---

### Post by The Patriot on 2009-02-16
How do I access the drive exactly? Can't this be done though the terminal via live CD?

---

### Post by The Patriot on 2009-02-16
```
ubuntu@ubuntu:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 695M  2.0M  693M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 695M  2.0M  693M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 695M     0  695M   0% /lib/init/rw
varrun                695M  104K  695M   1% /var/run
varlock               695M     0  695M   0% /var/lock
udev                  695M  2.7M  692M   1% /dev
tmpfs                 695M  148K  695M   1% /dev/shm
rootfs                695M   24M  671M   4% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 695M   12K  695M   1% /tmp
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5147e9d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10089    81039861    7  HPFS/NTFS
/dev/sda2           14093       14593     4024282+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3           12040       14092    16490722+   5  Extended
/dev/sda4           10090       12039    15663375    7  HPFS/NTFS
/dev/sda5           14001       14092      738958+  82  Linux swap / Solaris
/dev/sda6           12040       14000    15751669+  83  Linux

Partition table entries are not in disk order

```

---

### Post by x33a on 2009-02-16
i think you don't have a grub menu.lst on the jaunty partition (got deleted somehow?), and that's why you are getting the error.

i am not too sure, what are the options without that file.

maybe someone more knowledgeable  can help you out.

---

### Post by The Patriot on 2009-02-17
bump...anyone knows? :(

---

### Post by Ripose on 2009-02-19
The same thing happened to me.

I used the Win 7 DVD and the fix Windows option. My grub boot reappeared with Win 7 and Ubuntu on it, they both worked fine.

---

