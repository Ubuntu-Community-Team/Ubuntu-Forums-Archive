---
title: "Dual Boot XP Stopped Working"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2009-09-06
I have a dual-boot system Kubuntu 9.04 and Windows XP. The Windows boot option in grub stopped working - I now get the message (systemroot)\system32\hal.dll missing or corrupt. hal.dll is not missing, and I've tried replacing hal.dll, replacing boot.ini, and running fixboot from the windows recovery console, all to no avail. 

In my system, Kubuntu runs on Linux Software RAID with two disks, and Windows XP is on a partition on one of the two disks. Various relevant config files are below - note that this config worked for some time before it failed (BTW I suspect the cause of the failure could be from writing files to the WinXP partition from Linux, but that doesn't mean I know how to fix the problem).

Anyone know how to fix this?

-------------------------------
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000efd49                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   fd  Linux raid autodetect
/dev/sda2            6080       54953   392580405    5  Extended             
/dev/sda3   *       54954       60800    46966027+   7  HPFS/NTFS            
/dev/sda5            6080        6322     1951866   82  Linux swap / Solaris 
/dev/sda6            6323       54953   390628476   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000558d                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   fd  Linux raid autodetect
/dev/sdb2            6080       54953   392580405    5  Extended             
/dev/sdb5            6080        6322     1951866   82  Linux swap / Solaris 
/dev/sdb6            6323       54953   390628476   fd  Linux raid autodetect

Disk /dev/md0: 50.0 GB, 50001346560 bytes
2 heads, 4 sectors/track, 12207360 cylinders
Units = cylinders of 8 * 512 = 4096 bytes   
Disk identifier: 0x00000000                 

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 800.0 GB, 800006864896 bytes
2 heads, 4 sectors/track, 195314176 cylinders
Units = cylinders of 8 * 512 = 4096 bytes    
Disk identifier: 0x00000000                  

Disk /dev/md1 doesn't contain a valid partition table

-------------------------------
cat /boot/grub/menu.lst                                
# menu.lst - See: grub(8), info grub, update-grub(8)                      
#            grub-install(8), grub-floppy(8),                             
#            grub-md5-crypt, /usr/share/doc/grub                          
#            and /usr/share/doc/grub-doc/.                                

title           Ubuntu jaunty (development branch), kernel 2.6.28.9r2
root            (hd0,0)                                              
kernel          /vmlinuz-2.6.28.9r2 root=/dev/md1 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd          /initrd.img-2.6.28.9r2

title           Ubuntu jaunty (development branch), kernel 2.6.28.9r2 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.28.9r2 root=/dev/md1 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd          /initrd.img-2.6.28.9r2

title           Windows XP
root            (hd0,2)
makeactive
chainloader     +1

--------------------------------
$ cat /mnt/WinXP/boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows XP Professional" /fastdetect

-------------------------------------------
$ ls -l /mnt/WinXP/WINDOWS/system32/hal.dll
-rwxrwxrwx 1 root root 134400 2008-04-13 22:01 /mnt/WinXP/WINDOWS/system32/hal.dll

---

### Post by gus_zernial on 2009-09-07
After some research I solved my own problem, and I wanted 
to post the answer in case others encounter this. The answer 
was that I needed to change the boot.ini file to refer to partition 2 rather than partition 3. Altho /dev/sda3 is the actual Windows partition, apparently Windows does not consider extended partitions in their numbering scheme, so from Windows standpoint the installation is on Partition 2.

---

### Post by pythonscript on 2009-09-07
Thanks for the information! This will definitely come in useful as RAID becomes more popular.

---

