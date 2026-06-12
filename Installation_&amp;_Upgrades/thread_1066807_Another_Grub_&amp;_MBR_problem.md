---
title: "Another Grub &amp; MBR problem"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Unknown Source on 2009-02-11
Sorry to post another I-have-a-dualboot-problem question. 
This can probably be answered easily. 
Can you please help? 
Do I need to repair the XP MBR, is that the problem?
Thanks!

Problem: 
Can't boot if external HDD is disconnected. 

My system: 
Running XP on internal HDD. 
Linux on external USB HDD, which is devided in two partitions.

grub> find /boot/grub/stage1
 (hd1,4)
grub> setup (hd1)
Error 12: Invalid device requested


Results.txt gives the following Boot Info Summary: 

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files/dirs:   /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

---

### Post by zwygart on 2009-02-11
Hi and welcome to ubuntu. 

Along the infos you posted, you have installed ubuntu on the external HDD with the install utility, without checking where grub (the bootloader) will be installed. 
Here what is happened to your system, the bootloader of XP was moved (for any reason) to the external drive. The bootloader of XP on the internal HD is corrupted. GRUB went install on the internal HD to load Ubuntu on the external HD.

So when you boot grub looks on the external HD for his files. If it is not connected it gives error 21 I think. If you choose Ubuntu, it loads ubuntu normally. If you choose XP. It loads the bootloader of XP from the external to load internal XP. If you want you can disconnect your drive after having booted XP. But not when you boot ubuntu.

How to fix this?
To install GRUB on the external HD, you first need a primar partition on it. You have a ntfs partition with XP bootloader. Convert it ti a fat or ext partition. (This will erase your bootloader of XP). Run the commands root and setup again. This should work again.
To fix XP bootloader, look on meierfra tutorial. [http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

Please post the entire content of result.txt. ([http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/))

---

### Post by caljohnsmith on 2009-02-11
> **zwygart said:**
> 
So when you boot grub looks on the external HD for his files. If it is not connected it gives error 21 I think. If you choose Ubuntu, it loads ubuntu normally. If you choose XP. It loads the bootloader of XP from the external to load internal XP. If you want you can disconnect your drive after having booted XP. But not when you boot ubuntu.

Just curious, but how do you know that Grub is trying to boot Windows by loading "the bootloader of XP from the external to load internal XP?" There are no XP boot files in Unknown Source's sdb1 NTFS partition according to the script results.
> **zwygart said:**
> 
How to fix this?
To install GRUB on the external HD, you first need a primar partition on it. 
This is not true, you do not need a primary partition on the external drive in order to install Grub to the MBR (Master Boot Record) of the external drive. Grub can just as well have its boot files in a logical partition as well as a primary. 
[B]
Unknown Source[/B], how about trying the following:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
And then to restore a Windows MBR to your Windows drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
But according to the script results, it looks like your Windows partition is missing its boot.ini file, and also there are some issues with your Windows boot sector. Please post the *full* output of the latest Boot Info Script from [here]("https://sourceforge.net/projects/bootinfoscript/") so we can get a better idea of your setup.

---

### Post by Unknown Source on 2009-02-11
[QUOTE=zwygart;6716769]Hi and welcome to ubuntu. 

[SIZE="1"]*So when you boot grub looks on the external HD for his files. If it is not connected it gives error 21 I think. If you choose Ubuntu, it loads ubuntu normally. If you choose XP. It loads the bootloader of XP from the external to load internal XP. If you want you can disconnect your drive after having booted XP. But not when you boot ubuntu.*[/SIZE]

That's right. 

[SIZE="1"][I]How to fix this?
To install GRUB on the external HD, you first need a primar partition on it. You have a ntfs partition with XP bootloader. Convert it ti a fat or ext partition. (This will erase your bootloader of XP). Run the commands root and setup again. This should work again.
[/I][/SIZE]

If I change the NTFS partition, I will lose all stored data on there, so that's not an option I am affraid. 

To fix XP bootloader, look on meierfra tutorial. [http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

Recovery console does not work: installed version is newer than version on -original- CD. No option to be found in MS online help for XP SP3...

---

### Post by Unknown Source on 2009-02-11
@ caljohnsmith
Thanks for your reply!

[SIZE="1"][I]Unknown Source[/B], how about trying the following:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
[/I][/SIZE]

Done that now. 
Have not yet done the other you have suggested a part from installing lilo. 

Please have a look at the requested full report: 

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files/dirs:   /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    78,124,094    78,027,705   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54fc4954

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   758,284,064   758,284,002   7 HPFS/NTFS
/dev/sdb2         758,284,065   976,768,064   218,484,000   5 Extended
/dev/sdb5         758,284,128   973,747,844   215,463,717  83 Linux
/dev/sdb6         973,747,908   976,768,064     3,020,157  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D3-0A0D" TYPE="vfat" 
/dev/sda2: UUID="ACECB852ECB81892" TYPE="ntfs" 
/dev/sdb1: UUID="72D0233DD02306C7" TYPE="ntfs" 
/dev/sdb5: UUID="984ab289-d3da-4965-82e7-affdf553f680" TYPE="ext3" 
/dev/sdb6: UUID="86d07b28-340d-43ba-8db8-0a7f9d82396c" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/yfke/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=yfke)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=984ab289-d3da-4965-82e7-affdf553f680 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=86d07b28-340d-43ba-8db8-0a7f9d82396c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 397.5GB: boot/grub/menu.lst
 397.5GB: boot/grub/stage2
 397.5GB: boot/initrd.img-2.6.24-22-generic
 397.6GB: boot/initrd.img-2.6.24-22-generic.bak
 397.5GB: boot/initrd.img-2.6.27-11-generic
 397.5GB: boot/initrd.img-2.6.27-9-generic
 397.5GB: boot/vmlinuz-2.6.24-22-generic
 397.6GB: boot/vmlinuz-2.6.27-11-generic
 397.5GB: boot/vmlinuz-2.6.27-9-generic
 397.5GB: initrd.img
 397.5GB: initrd.img.old
 397.6GB: vmlinuz
 397.5GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  79 50 4a f5 00 00 00 00  |FILE0...yPJ.....|
00000010  01 00 01 00 38 00 01 00  c8 02 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  09 00 00 00 00 00 00 00  |................|
00000030  6a 13 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |j...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  d0 ed 37 b3 5f 91 c3 01  d0 ed 37 b3 5f 91 c3 01  |..7._.....7._...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  20 00 00 00 18 01 00 00  |........ .......|
000000a0  00 00 00 00 00 00 08 00  00 01 00 00 18 00 00 00  |................|
000000b0  10 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |.... ...........|
000000c0  00 00 00 00 00 00 01 00  00 00 00 00 01 02 00 00  |................|
000000d0  30 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |0... ...........|
000000e0  00 00 00 00 00 00 01 00  03 00 44 00 02 00 00 00  |..........D.....|
000000f0  80 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |.... ...........|
00000100  00 00 00 00 00 00 01 00  07 00 02 a0 01 02 00 00  |................|
00000110  80 00 00 00 20 00 00 1a  04 00 00 00 00 00 00 00  |.... ...........|
00000120  0f 00 00 00 00 00 0f 00  00 00 00 00 00 00 00 00  |................|
00000130  80 00 00 00 20 00 00 1a  27 73 00 00 00 00 00 00  |.... ...'s......|
00000140  10 00 00 00 00 00 01 00  00 00 00 00 00 00 00 00  |................|
00000150  80 00 00 00 20 00 00 1a  7a 7b 00 00 00 00 00 00  |.... ...z{......|
00000160  11 00 00 00 00 00 12 00  00 00 00 00 00 00 00 00  |................|
00000170  80 00 00 00 20 00 00 1a  ed 83 00 00 00 00 00 00  |.... ...........|
00000180  12 00 00 00 00 00 13 00  00 00 00 00 00 00 00 00  |................|
00000190  b0 00 00 00 20 00 00 1a  00 00 00 00 00 00 00 00  |.... ...........|
000001a0  00 00 00 00 00 00 01 00  06 00 00 00 00 00 00 00  |................|
000001b0  30 00 00 00 68 00 00 00  00 00 18 00 00 00 03 00  |0...h...........|
000001c0  4a 00 00 00 18 00 01 00  05 00 00 00 00 00 05 00  |J...............|
000001d0  d0 ed 37 b3 5f 91 c3 01  d0 ed 37 b3 5f 91 c3 01  |..7._.....7._...|
*
000001f0  00 b0 e0 00 00 00 00 00  00 a8 e0 00 00 00 6a 13  |..............j.|
00000200

---

### Post by caljohnsmith on 2009-02-11
So when you ran the script again, did you do it before doing the Grub commands? The script still shows your sdb drive as having a Windows MBR rather than Grub in the MBR. Also, if you want to be able to boot your Windows drive without having your external drive connected, I would recommend running the lilo command, because that installs a Windows equivalent MBR to your Windows drive. The other thing you will need to do is correct your Grub's menu.lst to boot from the external drive:
```
gksudo gedit /boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,4) instead of (hd1,4) similar to:
```
title Ubuntu 8.10, kernel 2.6.27-11-generic
root [COLOR="Blue"](hd0,4)[/COLOR]
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=984ab289-d3da-4965-82e7-affdf553f680 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet
```
Also change the "# groot..." line:
```
# groot=[COLOR="Blue"](hd0,4)[/COLOR]
```
And lastly, change your Windows entry at the end of the menu.lst to:
```
title       Windows XP
rootnoverify     (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, set your BIOS "boot order" so that your external drive boots before your Windows drive, and if all goes well you should be able to boot into Ubuntu. Also, when you disconnect the Ubuntu drive, you should be able to boot into Windows (but as I mentioned previously, there may be issues with your Windows partition). Let me know how it goes or if you run into problems.

---

### Post by Unknown Source on 2009-02-11
> **caljohnsmith said:**
> Let me know how it goes or if you run into problems.

It works brilliant now!
I am pouring you a nice cup of Ubuntu with rum!

Windows loads a bit slow now, not sure why. Maybe because of the boot.ini issue?
Anyway, I am happy now. 

Thanks again!

---

### Post by caljohnsmith on 2009-02-11
Glad to hear it's all working OK, although I would recommend repairing your Windows partition since it has some issues. First, how about downloading the attached "boot.ini.txt" file to your desktop and do:
```
sudo mount /dev/sda2 /mnt
sudo mv ~/Desktop/boot.ini.txt /mnt/boot.ini
```
Next, I would recommend using testdisk to repair your Windows XP boot sector, so first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the sda HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda2 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know if Windows boots any faster.

---

### Post by Unknown Source on 2009-02-11
Will give that a try tomorrow. 
Need to get some sleep now...

---

### Post by zwygart on 2009-02-12
Ok, I will give and have some precision caljohnsmith :
First I saw that GRUB had his files on external. Then grub from the external loads the files of XP of the internal bootloader XP. (GRUB files are on ext XP on int). Sorry for the confusion. But it seems to be right now. 

Second, I was unable to install syslinux on a logicall partition (is it?). So I presumed that stage1 from grub cannot be installed on a logical. Stage2 all right can be on logicall but not more than (hdX,9). My question : stage1 is installed where ? on MBR or bootsector? I tought that logicall did not have bootsectors?

Thanks for any answer. Thanks also for Unknown Source.

---

### Post by caljohnsmith on 2009-02-12
> **zwygart said:**
> 
Second, I was unable to install syslinux on a logicall partition (is it?). So I presumed that stage1 from grub cannot be installed on a logical. Stage2 all right can be on logicall but not more than (hdX,9). My question : stage1 is installed where ? on MBR or bootsector? I tought that logicall did not have bootsectors?

Thanks for any answer. Thanks also for Unknown Source.
I haven't tried installing syslinux to a logical partition, but the stage1 file of Grub can be installed to the MBR or the boot sector of any primary or logical partition; so yes, logical partitions have boot sectors just like primary partitions. :) From my experience, "boot sector" usually means the first sector of a partition, but I've seen where sometimes it can mean the first several sectors of the partition if the boot code takes up more than one sector.

Also, you might want to keep in mind that really the only difference between a logical partition and a primary partition is where the record of the partition is kept; all primary partitions are listed in the partition table in the MBR, whereas logical partitions are listed in the partition table in one of the linked-together EBRs (Extended Boot Records) associated with the logical partitions. It's worth noting that the structure of an EBR is basically the same as the MBR, except an EBR is located somewhere else on the HDD other than the first sector of the HDD (which is where the MBR always is). But the actual structure of a logical partition is no different than a primary partition, which is why it is possible to convert between the two by simply changing the partition table; i.e. you can convert a logical partition to a primary partition, or a primary partition to a logical partition by making the appropriate changes to the partition table, and assuming all the requirements are met. 

Also, Grub has the ability to put its boot files on any logical partition up to (hdX,255), because Grub uses a one-byte hex number to store the partition number; therefore the max is 0xFF or 255. Of course linux limits you to much less than 255 logical partitions, so that's the limiting factor. If you want any more specifics about technical details like that, forum member meierfra is the guy to ask. He's the one who wrote the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") and knows Grub inside-and-out. :)

---

