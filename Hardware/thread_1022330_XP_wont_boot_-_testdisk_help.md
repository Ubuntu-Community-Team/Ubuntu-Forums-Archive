---
title: "XP wont boot - testdisk help"
date: 2008-12-26
forum: Hardware
---

### Post by p4cldba on 2008-12-26
All,

This is a hp pavilion entertainment laptop with windows xp home edition . I was trying to make another  partition to install ubuntu using partitionmagic . but since then it wont boot .    I have few programs installed under Windows XP  which I really dont want to loose . I googled and came across testdisk utility but I am a newbie and feel not very comfortable  to use .  so I am looking for any advice/guidance  that will help me boot my XP . 

appreciate any help 

merry X'mas and happy new year .

thanks
pk

---

### Post by caljohnsmith on 2008-12-26
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your Windows problem might be.

---

### Post by p4cldba on 2008-12-26
Thank you so much for looking into my issue . . 

I did as you suggested . and here is the output 


============================= Boot Info Summary: ==============================

Gateway? is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  XP
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  XP
    Mounting failed:  
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda3 sda3 -o remove_hiberfile


=========================== Drive/Partition Info: =============================
fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   207800774   103900356    7  HPFS/NTFS
/dev/sda2       207816840   232332029    12257595    c  W95 FAT32 (LBA)
/dev/sda3       232332030   234436544     1052257+  d7  Unknown

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

_______________________________________________________________________________
blkid -c /dev/null:

/dev/sda1: UUID="37D790BC31D0F15C" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="3EC6-2E70" TYPE="vfat" 
/dev/sda3: UUID="801C09341C09272E" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=============================== StdErr Messages: ===============================

Unknown BootLoader  on /dev/sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 88 08 63 0c  |........?.....c.|
00000020  76 12 76 01 56 5d 00 00  00 00 00 00 02 00 00 00  |v.v.V]..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 70 2e c6 3e 20  20 20 20 20 20 20 20 20  |..)p..>         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.

---

### Post by caljohnsmith on 2008-12-26
OK, how about trying:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
And if that completes succesfully, try:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
nautilus /media/sda1 &
```
And if you get that far, you should be able to browse your Windows files with that last command. Let me know how it goes or if you run into problems.

---

### Post by p4cldba on 2008-12-26
i did as you suggested and now I am able to see my files in nautilus

ubuntu@ubuntu:~/Desktop$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~/Desktop$ sudosudo ntfsfix /dev/sda1
bash: sudosudo: command not found
ubuntu@ubuntu:~/Desktop$ sudo ntfsfix /dev/sda1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
ubuntu@ubuntu:~/Desktop$ sudo mkdir /media/sda1
ubuntu@ubuntu:~/Desktop$ sud mount /dev/sda1 /media/sda1
bash: sud: command not found
ubuntu@ubuntu:~/Desktop$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~/Desktop$ nautilus /media/sda1 &
[1] 10267
ubuntu@ubuntu:~/Desktop$ 


so does this mean that now I will be able to boot windows XP on the laptop  . and create another partition ?

---

### Post by caljohnsmith on 2008-12-27
Go ahead and try booting Windows, and if it doesn't work, let me know exactly what happens and what errors you might get. Also please post:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```

---

### Post by p4cldba on 2008-12-27
when i try to boot with windows . it does not . it end up with a blue screen  where the last line beginning with " stop 0x0000000024  ..  .  "


here is the output as suggested . i had to do a ntfsfix to cat the boot.ini.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /mnt ntfs-3g force 0 0



ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt


ubuntu@ubuntu:~$ ls -l /mnt/boot.ini
-rwxrwxrwx 1 root root 209 2008-11-28 04:52 /mnt/boot.ini

ubuntu@ubuntu:~$ cat /mnt/boot.ini
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

---

### Post by caljohnsmith on 2008-12-27
OK, if you have your Windows Install CD, how about booting that, go to the "recovery console", and run:
```
chkdsk /r
```
And run chkdsk as many times as it takes until it reports no errors. After that, reboot, and see if you get any further booting Windows. If it doesn't work, I would boot your Windows CD again, this time select the "install Windows" option, and after that the CD should give you a "Repair Windows" option; I the "Repair Windows" option is your best bet if chkdsk doesn't correct the problem. Let me know how it goes though.

---

### Post by p4cldba on 2008-12-27
this laptop came with windows xp pre installed . I only have a windows xp professional cd . when i try to boot with the windows xp professional cd and  try to do repair it do not detect the hard disk.  so i was wondering if the testdisk utility will be the savior .

---

### Post by caljohnsmith on 2008-12-27
> **p4cldba said:**
> this laptop came with windows xp pre installed . I only have a windows xp professional cd . when i try to boot with the windows xp professional cd and  try to do repair it do not detect the hard disk.  so i was wondering if the testdisk utility will be the savior .
I don't think testdisk can help you with the Windows problem you are experiencing. I think you will need the Windows Install CD for that. At least you have access to your Windows files, so could you save your personal files and install XP professional instead?

---

### Post by p4cldba on 2008-12-27
I tried now with windows xp professional cd to install again . and this is the message it shows

Windows XP Professional Setup
---------------------------------------------
Setup did not find any hard disk drives installed in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacture-supplied diagnostic or setup program.

Setup cannot continue. To quit Setup , press F3.

---

### Post by caljohnsmith on 2008-12-27
Is your HDD IDE or SATA? I would think it would be IDE, but if it is SATA, you'll need drivers for it in order for the Windows CD to recognize it. Another thing to check would be to go into your BIOS and if you have "AHCI" enabled, you could disable it and see if that gets the XP CD to work. The only other thing I can think of is if the HDD's partition table is corrupt, and the script results you posted showed that the partition table was using different CHS values than what Linux would expect, but I'm not sure if that would be a problem for the Windows CD (I doubt it, but you never know with Windows).

---

### Post by p4cldba on 2008-12-27
this is a hp pavilion dv6135nr entertainment notebook pc . 

Ok . I disabled SATA on the BIOS after that the windows XP cd is able to detect the hard disk . 

C:  partition1 [unknown1]            101465MB(101465 MB free)
    Unpartitioned space                   8MB
D:  Partition2(HP_RECOVERY) [FAT32]   11970MB ( 1232 MB free)
F:  Partition3 [NTFS]                  1028MB (  226 MB free)


So now i don't understand why it shows C: as unknown partition . ubuntu is able to detect and show all the files in it . and also i am not able to know why there are so many partitions in this laptop :(

---

### Post by caljohnsmith on 2008-12-27
OK, how about first posting:
```
sudo lshw -C disk
```

---

### Post by p4cldba on 2008-12-27
ubuntu@ubuntu:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: FUJITSU MHV2120B
       vendor: Fujitsu
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 892C
       serial: NW9XT6A2KKTT
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=282d282d
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-851S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-27
> **p4cldba said:**
> 
C:  partition1 [unknown1]            101465MB(101465 MB free)
    Unpartitioned space                   8MB
D:  Partition2(HP_RECOVERY) [FAT32]   11970MB ( 1232 MB free)
F:  Partition3 [NTFS]                  1028MB (  226 MB free)


So now i don't understand why it shows C: as unknown partition . ubuntu is able to detect and show all the files in it . and also i am not able to know why there are so many partitions in this laptop :(
The three partitions you show above are as expected, because your fdisk output in Ubuntu shows exactly the same thing. Just tell the Windows install CD to install Windows to the C: drive above, and you should be fine. It's OK that Windows doesn't recognize the partition, because Windows will overwrite it anyway; just make sure to first move all your important documents that are in your current Windows partition to some other drive, because everything will be deleted in your current Windows partition when you reinstall. Good luck, and let me know how it goes.

---

