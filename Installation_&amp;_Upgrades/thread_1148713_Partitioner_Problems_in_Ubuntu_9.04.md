---
title: "Partitioner Problems in Ubuntu 9.04"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by meccamw on 2009-05-04
Can someone explain (or point me to a good document) that explains the various partition options when installing Ubuntu 9.04? I'm afraid that this section of the installer makes the least amount of sense to me. So far, the only sucess I've had installing Ubuntu is on my laptops where it is the only thing running. Whenever I've installed it on my desktop where it needs to share with Windows XP I veer into never-never land.
Right now, after about 7-8 retries, I've got an XP partition that takes up most of my one hard drive and Ubuntu that takes up approv 2 1/5 gb. I asked it to install Ubuntu side by side with an existing operating system but I'm bemused on how it decided to carve up the drive.
 
I've also tried manually selecting the partitiion options and when I do so I do seem to get things installed but GRUB doesn't run when I reboot and I go right into XP.
 
I'm thinking that my main problem is that I have three drives in my system (two IDE drives and 1 SATA drive). The reason I think this is that when I originally had Ubuntu 8.04 and XP on the system it tried to install on my SATA drive which is NOT where I had XP installed on. I managed to get it working but even then I wasn't sure what the installer was doing.
 
Can anybody point me in the right direction? Can this be a simple matter of having crossed wires in my BIOS with these three drives?
 
Thanks
 
Mark

---

### Post by Pumalite on 2009-05-04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by dabl on 2009-05-04
Pumalite's links are excellent.

Also, FWIW, I've always found it a more understandable process to use a separate Live CD to do the partitioning job in advance of installing Linux, and then to use the *buntu Alternate Install CD to install the OS -- you can go directly to "manual partitioning" and simply set the mount points and move on.  Here's a good choice:

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by meccamw on 2009-05-04
I actully did use gparted on the Ubuntu livecd to partition my drive.  However, I don't believe I used the manual partition option when installing.  Can you give me any pointers how to use the mount points?

---

### Post by networm1230 on 2009-05-04
> **meccamw said:**
> Can someone explain (or point me to a good document) that explains the various partition options when installing Ubuntu 9.04? I'm afraid that this section of the installer makes the least amount of sense to me. So far, the only sucess I've had installing Ubuntu is on my laptops where it is the only thing running. Whenever I've installed it on my desktop where it needs to share with Windows XP I veer into never-never land.
Right now, after about 7-8 retries, I've got an XP partition that takes up most of my one hard drive and Ubuntu that takes up approv 2 1/5 gb. I asked it to install Ubuntu side by side with an existing operating system but I'm bemused on how it decided to carve up the drive.
 
I've also tried manually selecting the partitiion options and when I do so I do seem to get things installed but GRUB doesn't run when I reboot and I go right into XP.
 
I'm thinking that my main problem is that I have three drives in my system (two IDE drives and 1 SATA drive). The reason I think this is that when I originally had Ubuntu 8.04 and XP on the system it tried to install on my SATA drive which is NOT where I had XP installed on. I managed to get it working but even then I wasn't sure what the installer was doing.
 
Can anybody point me in the right direction? Can this be a simple matter of having crossed wires in my BIOS with these three drives?
 
Thanks
 
Mark

I am not so shore but this may help you [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

---

### Post by meccamw on 2009-05-04
Well, nosing around those sites I realized that there is a slider at the bottom of the partition setup screen.  Moving it around now allows me to select a Ubuntu install greater than 4gb.  GRUB is also coming up and allowing me to select Windows XP and Ubuntu.

However, now when I select XP I get:
NTLDR not found

I can, however, get into Ubuntu 9.04.

XP looks like it is still there but I can't seem to get into it via  GRUB.

---

### Post by caljohnsmith on 2009-05-05
If you want some help booting XP from Grub, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by meccamw on 2009-05-05
> **caljohnsmith said:**
> If you want some help booting XP from Grub, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John
Yeah, I already did that previously as I saw it being requested in previous threads however I'm not able to interpret it.   Hopefully you can.  
I have three drives in my system.  Two ide drives (SDB is the one with XP and Ubuntu on it) and one SATA drive.  This seems to be confusing GRUB and the installer for some reason.
Here it is:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10f2b6f6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   290,728,304   290,728,242   7 HPFS/NTFS
/dev/sda2         290,728,305   586,067,264   295,338,960   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sdb2         268,414,020   273,522,689     5,108,670  83 Linux
/dev/sdb3         273,522,690   586,067,264   312,544,575   5 Extended
/dev/sdb5         273,522,753   580,058,954   306,536,202  83 Linux
/dev/sdb6         580,059,018   586,067,264     6,008,247  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13e3d5f0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   320,159,384   320,159,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1290528590526F6B" LABEL="SeagateSATA_300" TYPE="ntfs" 
/dev/sda2: UUID="475984CF30202C10" TYPE="ntfs" 
/dev/sdb1: UUID="B4D8EE1CD8EDDD1C" TYPE="ntfs" 
/dev/sdb2: UUID="b27c7bb1-677f-4eaa-82b7-32b305d98751" TYPE="ext2" 
/dev/sdb5: UUID="be18e58a-59b9-4936-ae23-c956843256b4" TYPE="ext3" 
/dev/sdb6: UUID="56eba200-a8d3-451c-a12e-2347797f8d81" TYPE="swap" 
/dev/sdc1: UUID="320C8D630C8D2349" LABEL="MAXTORIDE_160" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/meccamw/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=meccamw)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=be18e58a-59b9-4936-ae23-c956843256b4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=be18e58a-59b9-4936-ae23-c956843256b4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        be18e58a-59b9-4936-ae23-c956843256b4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=be18e58a-59b9-4936-ae23-c956843256b4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        be18e58a-59b9-4936-ae23-c956843256b4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=be18e58a-59b9-4936-ae23-c956843256b4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        be18e58a-59b9-4936-ae23-c956843256b4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=be18e58a-59b9-4936-ae23-c956843256b4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=56eba200-a8d3-451c-a12e-2347797f8d81 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 153.1GB: boot/grub/menu.lst
 153.1GB: boot/grub/stage2
 153.1GB: boot/initrd.img-2.6.28-11-generic
 153.1GB: boot/vmlinuz-2.6.28-11-generic
 153.1GB: initrd.img
 153.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  f0 d5 e3 13 00 00 00 01  |................|
000001c0  01 00 07 fe ff ff 3f 00  00 00 5a 3e 15 13 00 00  |......?...Z>....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by caljohnsmith on 2009-05-05
Since you have Grub installed to the MBR of two of your drives, I don't know for sure which drive you are booting on start up. That means there are a couple possible Grub entries for booting Windows, so how about trying the following entries in your menu.lst:
```
title        Microsoft Windows XP Home Edition (hd2)
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

title        Microsoft Windows XP Home Edition (hd0)
rootnoverify    (hd0,0)
chainloader    +1

```
One of those should work to boot Windows, but if not, let me know exactly what happens when you choose each one from the Grub menu. We can work from there if necessary.

John

---

### Post by meccamw on 2009-05-05
Dagnabbit.  Thought I had it.  The first one only gave me 'Starting up....' and stopped there.  I gave it a minute or two and then rebooted.
The second one gave me the XP Startup graphic but it only stayed on for about 2 seconds and then a blue screen came up indicating that the system was stopped to prevent damaging my computer.

I don't know how GRUB came to be on two drives.  I'll have to figure out how to delete it.

---

### Post by caljohnsmith on 2009-05-06
Have you tried running a "chkdsk" on your Windows partition? If you haven't, how about booting your Windows Install CD, go to the "recovery console" and do:
```
map
```
That will show a list of your partitions and corresponding drive letters. Find the one that is your Windows installation (should most likely be "C") and do:
```
chkdsk /r C:
```
And run the chkdsk command as many times as it takes until it reports no errors. Then try booting Windows again using the second entry I gave in my last post, and let me know if anything changes. 

John

---

### Post by meccamw on 2009-05-06
> **caljohnsmith said:**
> Have you tried running a "chkdsk" on your Windows partition? If you haven't, how about booting your Windows Install CD, go to the "recovery console" and do:
```
map
```
That will show a list of your partitions and corresponding drive letters. Find the one that is your Windows installation (should most likely be "C") and do:
```
chkdsk /r C:
```
And run the chkdsk command as many times as it takes until it reports no errors. Then try booting Windows again using the second entry I gave in my last post, and let me know if anything changes. 

John
I'll give that a try.  it is reporting errors but I haven't been able to run it enough times yet where it runs clean.  It is doing something odd:  It gets up to 72% complete quickly and then mysteriously returns to 50% complete and then takes it merry time before it finishes.

---

### Post by meccamw on 2009-05-06
> **caljohnsmith said:**
> Have you tried running a "chkdsk" on your Windows partition? If you haven't, how about booting your Windows Install CD, go to the "recovery console" and do:
```
map
```
That will show a list of your partitions and corresponding drive letters. Find the one that is your Windows installation (should most likely be "C") and do:
```
chkdsk /r C:
```
And run the chkdsk command as many times as it takes until it reports no errors. Then try booting Windows again using the second entry I gave in my last post, and let me know if anything changes. 

John
Nope.  No joy.  I ran chkdsk several times until it reported no errors.  When I rebooted and selected the HD0 option the Windows XP banner came up for about two seconds before the moving bar froze and the blue screen came up. 

Any other ideas?

---

### Post by caljohnsmith on 2009-05-06
When you boot Windows, can you press F8, and is there some option about booting from last known working configuration? Or maybe an option to restore last known working configuration? I can't remember exactly what options you get when you press F8 on start up, but it's something like that. Let me know if that works at all.

John

---

### Post by xerex8 on 2009-05-07
I have the same problem as youres. what I did is boot in XP, download Easus partition editor and resize your XP partition to what ever you like. To check if it is working, reboot. If it is ok, run Ubuntu install again. Thats solve my problem.

---

### Post by meccamw on 2009-05-07
> **caljohnsmith said:**
> When you boot Windows, can you press F8, and is there some option about booting from last known working configuration? Or maybe an option to restore last known working configuration? I can't remember exactly what options you get when you press F8 on start up, but it's something like that. Let me know if that works at all.

John
Yes, I tried that as well.  I tried a safe boot, boot from last good working config, and boot as normal.  All came up with the same blue screen indicating that the system was shut down to prevent damage to the system.
 
I don't have anything installed yet in either Ubuntu or XP.  Do you think it would be a good idea to reformat the entire drive and re-install both operating systems?  I've already lost my good XP setup last week so I have nothing to lose with this.

---

### Post by meccamw on 2009-05-07
> **xerex8 said:**
> I have the same problem as youres. what I did is boot in XP, download Easus partition editor and resize your XP partition to what ever you like. To check if it is working, reboot. If it is ok, run Ubuntu install again. Thats solve my problem.
How did you get into XP in the first place to do this?  I'll check out Easus but I'm not sure what it does that Gparted and the partition editor in the Ubuntu installer didn't do.

---

### Post by caljohnsmith on 2009-05-07
> **meccamw said:**
> 
I don't have anything installed yet in either Ubuntu or XP.  Do you think it would be a good idea to reformat the entire drive and re-install both operating systems?  I've already lost my good XP setup last week so I have nothing to lose with this.
Yes, I think that reinstalling XP and Ubuntu to your 300 GB drive would be a good idea at this point since you say that is a viable option for you. I would suggest setting up all your partitions ahead of time by booting your Live CD and using gparted (System > Admin > Partition Editor). I would set up the first primary partition for Windows, and then I would create an extended partition with the rest of the space; in the extended partition I would create a logical partition for Ubuntu and a logical partition for swap space. After that, I would reinstall XP (make sure it boots OK after reinstalling it), and then I would reinstall Ubuntu. Also, when you go through the Ubuntu installer, click on the "advanced" button near the end of the installation process, and specify to have Grub installed to "/dev/sdb", which should be the 300 GB drive you are installing Ubuntu and XP to. Once everything is installed, just make sure you set your BIOS to boot the 300 GB XP/Ubuntu drive first on start up, and hopefully everything should work just fine. Let me know how it goes or if you run into problems.

John

---

### Post by meccamw on 2009-05-07
I will do so.  I actually have done the advanced setting with GRUB that you indicate so it would go to /dev/sbd.
The only thing I am unsure of is how to tell the installed to install Ubuntu into the partitions you indicate.

---

### Post by caljohnsmith on 2009-05-07
> **meccamw said:**
> 
The only thing I am unsure of is how to tell the installed to install Ubuntu into the partitions you indicate.
When you go through the installer, click the "manual" partition option, then right-click the partition you want to install Ubuntu to and select "edit partition"; there you can specify the mount point to be "/". You don't have to do anything with the other partitions, including the swap partition. Click the proceed/continue button, and that should be all there is to it. :)

John

---

### Post by meccamw on 2009-05-07
Ok, success.  I've got both Ubuntu and XP loaded on the same drive and I'm able to boot into both from grub.  The only thing I had wrong was that I still got the NTLDR not found error but I replaced the menu with 
title        Microsoft Windows XP Home Edition (hd0)
rootnoverify    (hd0,0)
chainloader    +1

from your previous note and bingo it worked.  What is the difference from your menu as regards to the one that grub used?  

Also, during the install what was the purpose of the / mount point that I used?

---

### Post by caljohnsmith on 2009-05-07
> **meccamw said:**
> Ok, success.  I've got both Ubuntu and XP loaded on the same drive and I'm able to boot into both from grub.  The only thing I had wrong was that I still got the NTLDR not found error but I replaced the menu with 
title        Microsoft Windows XP Home Edition (hd0)
rootnoverify    (hd0,0)
chainloader    +1

from your previous note and bingo it worked.  What is the difference from your menu as regards to the one that grub used?  

That's great news you've got XP and Ubuntu booting again. About your Windows XP Grub entry, sometimes the Ubuntu installer is not smart enough to realize that Windows is on (hd0) if you install Grub to the MBR of the same drive that Windows is on.
> **meccamw said:**
> 
Also, during the install what was the purpose of the / mount point that I used?
When you install Linux, you don't have to put its full file system in one partition like is the usual for Windows; instead you can put different system directories on different partitions. "/" is the root directory for Linux, meaning the full file system, so that is what you use for your main Ubuntu partition. If you don't specify any other mount points on other partitions (for instance having a "/boot" partition), then your full Ubuntu file system will end up in the partition specified as the root or "/" partition. 

Anyway, glad it's all working. :)

Cheers,
John

---

### Post by meccamw on 2009-05-08
> **caljohnsmith said:**
> That's great news you've got XP and Ubuntu booting again. About your Windows XP Grub entry, sometimes the Ubuntu installer is not smart enough to realize that Windows is on (hd0) if you install Grub to the MBR of the same drive that Windows is on.
 
When you install Linux, you don't have to put its full file system in one partition like is the usual for Windows; instead you can put different system directories on different partitions. "/" is the root directory for Linux, meaning the full file system, so that is what you use for your main Ubuntu partition. If you don't specify any other mount points on other partitions (for instance having a "/boot" partition), then your full Ubuntu file system will end up in the partition specified as the root or "/" partition. 
 
Anyway, glad it's all working. :)
 
Cheers,
John
 Undrstood.  However, I did try using the HD setting you provided before I submitted a note on this forum but it didn't work.  Your suggestion eliminated some commands (I believe GRUB was issuing some MAP commands) and I was just wondering what the difference was and why my HD setting didn't work but your mods did.
 
Thanks for the help.

---

