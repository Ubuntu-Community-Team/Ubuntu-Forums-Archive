---
title: "Grub won't install/ Dual boot setup"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by MGaddict2000 on 2009-08-10
I am attempting to install Jaunty on a new computer. I have an ASUS P6T mobo and a Seagate 1.5T HD. (plus a bunch of other really fun toys not pertinent to mention.) I installed Windows 7 with no problems leaving 200GB to install Jaunty. During install, I created an 8GB swap partition and used the rest for linux. I then set it up to install Grub to the linux partition based on advice from some other sites and then to use EasyBCD to edit the windows boot loader. From my research, this seems to be the easest way to set up the dual boot. Unfortunatly, when it gets to installing Grub, I get a fatal error. I tried opening a terminal window from the Live CD and typing in ...
```
sudo grub-install /dev/sda4
```
Then I get the message...
```
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```
Anybody got a clue what to do? I'm not finding anybody else having the problem. It seems to just be me. :confused:

---

### Post by louieb on 2009-08-10
Probably something simple.
Run the script and put the results.txt in your next post.

[Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

---

### Post by MGaddict2000 on 2009-08-10
> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1fb11fb0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 2,520,678,824 2,520,471,977   7 HPFS/NTFS
/dev/sda3       2,913,580,530 2,930,272,064    16,691,535   5 Extended
/dev/sda5       2,913,580,593 2,930,272,064    16,691,472  82 Linux swap / Solaris
/dev/sda4       2,520,678,825 2,913,580,529   392,901,705  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C63445D33445C761" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="7CEE62EBEE629CE0" TYPE="ntfs" 
/dev/sda4: UUID="b625d66b-0386-4df5-941f-4283bf6a2ac3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5865fe62-9f10-4e11-bd42-a47d04345332" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=b625d66b-0386-4df5-941f-4283bf6a2ac3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5865fe62-9f10-4e11-bd42-a47d04345332 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


1305.7GB: boot/grub/stage2
1305.8GB: boot/initrd.img-2.6.28-11-generic
1305.8GB: boot/vmlinuz-2.6.28-11-generic
1305.8GB: initrd.img
1305.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

And thanks for the speedy reply. That was less than an hour.

---

### Post by louieb on 2009-08-10
This is what I was looking for

> 
=================== sda4: Location of files loaded by Grub:
1305.7GB: boot/grub/stage2
1305.8GB: boot/initrd.img-2.6.28-11-generic
1305.8GB: boot/vmlinuz-2.6.28-11-generic
1305.8GB: initrd.img
1305.8GB: vmlinuzTo put GRUB's stage1 code in the boot sector of sda4
```
sudo grub
```at the **grub>** prompt

```
root (hd0,3)
setup (hd0,3)
quit
```

---

### Post by MGaddict2000 on 2009-08-10
> ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,3)
root (hd0,3)

Error 18: Selected cylinder exceeds maximum supported by BIOS
grub> setup (hd0,3)
setup (hd0,3)

Error 12: Invalid device requested
grub> quit


I'm guessing this isn't the response I'm supposed to get. Interesting note: during the install it kept refering to my HD as SCSI3. I found that odd. I have the Hard drive configured as a IDE in the BIOS, which is the default. I forgot to change it before I installed win7 and I couldn't change it afterwards. I have no clue if that has any bearing on this. Could this be a BIOS problem?  Also note: before I installed win7, I originally had jaunty 64 installed by itself and it ran fine except it only acknowledged 4GB RAM. I reformatted the whole HD to install win7 because I couldn't get win7 to install with ubuntu already there.

---

### Post by louieb on 2009-08-10
It has been awhile since I see this
> Error 18: Selected cylinder exceeds maximum supported by BIOSUse to be that this error would show when drives larger that 8GB came out. BIOS would not allow booting an OS further that 8GB from the start of the disk. Then later the limit go raised to 33GB or so from the start.   
Drives go bigger and new BIOS came out to keep up. 

Don't know what the limit of modern BIOS is today but your  Ubuntu install is over it.  

The traditional fix is to create a separate /boot partition close enough to the start of disk to allow booting. 

See if there is a BIOS upgrade for your motherboard. Drives are getting larger again,  gee 1.5TB.  The only other thing I could suggest is re-partitioning the drive and putting the Ubuntu install closer to the start.

---

### Post by Flapse on 2009-08-10
Hey!

I've got kinda the same problem. When I look in the log I've created, I find this:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 1397691584 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x588bb61c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,799,999   204,593,152   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6595e79b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    19,535,039    19,534,977  82 Linux swap / Solaris
/dev/sdb2    *     19,535,040 1,465,144,064 1,445,609,025  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x449f449e

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="1cc83018-8433-41ec-982a-8fefc06903fd" TYPE="swap" 
/dev/sdb2: UUID="6a4ab99c-bd97-4803-b5d7-46a4ac8ba0f4" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  dc 80 45 8e 18 a9 91 65  aa f4 13 c1 53 69 f9 e7  |..E....e....Si..|
00000010  54 a5 12 4f ac 29 d8 94  f8 e4 7d 91 e5 ea df 0a  |T..O.)....}.....|
00000020  bd ad 73 6d 42 cc 6b 34  dc 0c 36 57 2a 03 fa 57  |..smB.k4..6W*..W|
00000030  cc 96 3a 66 40 6d 75 ff  00 2f 7f fe 70 96 cf 44  |..:f@mu../..p..D|
00000040  af 4a 6a 99 ef 21 3e bc  37 79 cd a7 cb 59 8e d8  |.Jj..!>.7y...Y..|
00000050  ec 3c a4 68 b3 17 95 51  44 9a 5f 48 5b 83 a7 90  |.<.h...QD._H[...|
00000060  f6 fa bd 87 01 68 f6 b6  29 94 9a a1 96 3f 39 8f  |.....h..)....?9.|
00000070  d8 ef f7 c6 04 3a 95 91  f0 1f 46 95 29 4b 1d 44  |.....:....F.)K.D|
00000080  13 28 2c ba 99 27 46 df  c6 c5 7f 56 1d 56 9e d5  |.(,..'F....V.V..|
00000090  e9 b0 d6 cb 78 6e aa 3c  af 33 8f c9 82 cd 50 68  |....xn.<.3....Ph|
000000a0  fd 3e c3 ac 72 73 06 d7  b2 ae fc af dd 87 5c 55  |.>..rs........\U|
000000b0  bb 5b cd 43 5f 4c 9d 17  e6 33 66 93 e6 f4 31 b5  |.[.C_L...3f...1.|
000000c0  60 ad 58 52 58 01 0a 62  96 38 e3 86 39 39 80 62  |`.XRX..b.8..99.b|
000000d0  28 83 51 27 b0 db b5 d4  f6 47 b5 4d 30 65 8d 6a  |(.Q'.....G.M0e.j|
000000e0  41 93 f4 71 25 2e a7 cc  58 16 f4 22 8d ae 97 d8  |A..q%...X.."....|
000000f0  da 59 06 ed d9 ee 5e 67  d2 d8 e1 7c d3 4b 1c e4  |.Y....^g...|.K..|
00000100  df 47 1f 66 21 a1 34 a4  68 17 42 ae db a9 ee 51  |.G.f!.4.h.B....Q|
00000110  ca fc f7 df c7 7c 2b 90  e2 1f 81 72 c1 5b c5 f9  |.....|+....r.[..|
00000120  5a 48 ab 28 cb e9 ea ab  e5 0c 01 0b a8 24 14 df  |ZH.(.........$..|
00000130  d6 12 1e b2 3f 0d 1a 86  e3 06 53 b7 39 27 54 b2  |....?.....S.9'T.|
00000140  cf b3 4e 15 c9 ab 9b 5d  66 5f 45 55 25 ac 1e 6a  |..N....]f_EU%..j|
00000150  78 a4 71 b5 b6 77 42 c3  ef e2 f2 f1 7e 48 73 a2  |x.q..wB.....~Hs.|
00000160  ac 82 0a 7e 19 a3 86 48  21 32 c2 d5 91 3b 18 d4  |...~...H!2...;..|
00000170  b1 31 55 cf 1e ed 6b 9f  37 0b eb 07 99 2d e4 bd  |.1U...k.7....-..|
00000180  c1 39 45 37 90 cd d6 41  0b 9f 2b 9b 76 45 63 6b  |.9E7...A..+.vEck|
00000190  27 88 c2 fc 70 75 9e de  54 9f d2 c5 14 6b c4 19  |'...pu..T....k..|
000001a0  90 44 d0 a2 ae 7b 58 59  47 68 f9 a0 77 62 a3 3d  |.D...{XYGh..wb.=|
000001b0  cb d4 69 f5 80 53 3a 61  aa a1 68 4f 7d 15 65 19  |..i..S:a..hO}.e.|
000001c0  6d 77 10 c3 4d 5c 2a 0f  d6 e6 a6 ea ca f5 66 68  |mw..M\*.......fh|
000001d0  65 46 64 a9 0c 0d e2 78  fc 2c 75 0d f6 38 98 be  |eFd....x.,u..8..|
000001e0  b0 f4 cf 5d 04 49 4c da  11 16 da 6d a4 05 f4 87  |...].IL....m....|
000001f0  86 2c b6 51 ab 3e 50 95  56 ca c7 d5 8a f3 d3 2a  |.,.Q.>P.V......*|
00000200


```

I've got 3 discs.
It seems to say that I've got Windows installed on Sda and sdb. And it states that sdc is empty (?) It also states that I've installed Ubuntu on sdb2. 
When I installed, I selected Sdb, because it seemed to be the empty disc. 
I can still boot windows 7...So I cant have overwritten it...
Got any help for me as well? :)
Thanks!!

---

### Post by raymondh on 2009-08-10
A good reference material, including possible fixes, is Herman's site.  [This is for grub error 18]("http://members.iinet.net.au/~herman546/p15.html#18").

Depending on the vintage of the BIOS, the cylinder limits can either be 8GB or 136GB.  As Louieb said, the fix is either to create a boot partition in front of the disk or, install the OS and GRUB within those limits.

Good luck.

---

### Post by louieb on 2009-08-10
> **Flapse said:**
> ...I've got kinda the same problem. When I look in the log I've created, I find this:

Yours isn't quite the same problem. Best advise I can give is start your own thread. I would just get to confusing to keep up with yours and MGaddict2000 	 		 posts and answers.  Looks like you may have partition table problems. or the script doesn't know what a Win 7 boot loader looks like. guess I should run it on my PC with 7 and find out.   Is this an Apple? Anyway in your new thread go ahead and include the results.txt file and type of computer.

---

### Post by MGaddict2000 on 2009-08-10
Well, thanks for the replys. I'm going to do some research into this. I'm guessing I was right in suspecting that it's because my hd is set up as IDE. There has never been a 1.5TB IDE hd and I'm betting the BIOS isn't liking it. If I find the answer, I'll post back with the solution. Looks like I get to bug ASUS now. 

And just so people aren't confused, this is a pretty new computer. Only 5 months old. 
ASUS P6T motherboard
Intel Core i7 920
BFG Tech GeForce GTX 285
6GB Corsair DDR3 1800 RAM
Lite-on BLueray burner
Seagate 1.5TB hd
Antec 1200 case

---

### Post by MGaddict2000 on 2009-08-20
well, nobody seems to have an answer for me other then I shouldn't be getting this error. That's no help. So I went ahead and followed the direction I found....

You don't have to, but I used GParted Live to edit my partitions. I like this method because it boots quickly and does exactly what it's supposed to do.
I deleted the Linux partitions. Then I moved my windows NTFS partition down 200MB (found out later only needed like 50MB but live and learn.) This took all night.
Then I created a new primary partition in the gap.
When I reinstalled Ubuntu, I set this partition as /boot. 
Then I had to make my swap and / directories as extended partitions. Then I used the advanced key and had grub install to the /boot partition. Install went fine. System booted into Linux, no prob. But then Win7 wouldn't boot.
I found a Vista 64x recovery CD on Microsoft.com (I could have used my original win7 install CD if I hadn't given it away.) Booted to that and went to repair windows installation. This found the problem immediately and took about 5 minutes to fix it. rebooted, now it only booted into win7. So I put my GParted live CD back in and had to reset flag on the Linux /boot partition to make it the bootable partition.

Overall, a huge pain, but it works great. And no, I'm no genius, It took me 2 days to figure it all out. Also, I wouldn't make a boot partition bigger then 100MB. This is a lot more then you need but it allows room to grow, and if you're working with a 1.5TB drive, it's not like a huge loss of space.

Good learning experience for me. If you are having this problem and need more clarification on anything, let me know, I've gotten pretty proficient at this now.

---

