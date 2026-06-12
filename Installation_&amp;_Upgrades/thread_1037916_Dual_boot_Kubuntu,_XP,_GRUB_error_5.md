---
title: "Dual boot Kubuntu, XP, GRUB error 5"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by jimmyboy76453 on 2009-01-12
I am a pretty green newbie, and I am trying to dual-boot Kubuntu and Windows XP to separate hard drives on the same computer.
I have a Dell Dimension 3000 (a rock and chisel set up, I know) with Windows XP on it, around 40 Gig. A while ago, I added an additional Maxtor 200 Gig Hard drive as the slave with the original drive as the master. 
Then I installed Kubuntu on the slave using the guided partition option and taking the entire drive. Everything seemed to install ok, but when I reboot, I get the message that GRUB is loading, then it says "Error 5", which I understand is a partition problem and is "a bad sign."
I downloaded SuperGrubDisk and ran it to uninstall GRUB so Windows will boot normally. Now how do I either fix GRUB or install a different boot loader to run either Windows or Kubuntu?

Sorry, I'm SO new, I don't even know if this makes sense. If I used wrong terminology, I'm sorry.

---

### Post by caljohnsmith on 2009-01-12
Hi jimmyboy76453, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by jimmyboy76453 on 2009-01-12
```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390    70766324    35334967+   7  HPFS/NTFS
/dev/sda3        70766325    78108029     3670852+  db  CP/M / CTOS / ...

sfdisk -V /dev/sda:

partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8d9d8d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   395295389   197647663+  83  Linux
/dev/sdb2       395295390   398283479     1494045    5  Extended
/dev/sdb5       395295453   398283479     1494013+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-0A10" TYPE="vfat" 
/dev/sda2: UUID="90EC9BC2EC9BA150" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sdb1: UUID="10044b40-bfcc-41f3-bbee-7dc0473242b6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="02aa2375-9734-4152-ac50-59696c45f9ec" TYPE="swap" 
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

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=10044b40-bfcc-41f3-bbee-7dc0473242b6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=10044b40-bfcc-41f3-bbee-7dc0473242b6

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		10044b40-bfcc-41f3-bbee-7dc0473242b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=10044b40-bfcc-41f3-bbee-7dc0473242b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		10044b40-bfcc-41f3-bbee-7dc0473242b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=10044b40-bfcc-41f3-bbee-7dc0473242b6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		10044b40-bfcc-41f3-bbee-7dc0473242b6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=10044b40-bfcc-41f3-bbee-7dc0473242b6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=02aa2375-9734-4152-ac50-59696c45f9ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11960
drwxr-xr-x  3 root root    4096 2009-01-12 00:40 .
drwxr-xr-x 20 root root    4096 2009-01-12 00:40 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-12 00:41 grub
-rw-r--r--  1 root root 8188826 2009-01-12 00:40 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-12 00:41 .
drwxr-xr-x 3 root root   4096 2009-01-12 00:40 ..
-rw-r--r-- 1 root root    197 2009-01-12 00:40 default
-rw-r--r-- 1 root root     30 2009-01-12 00:40 device.map
-rw-r--r-- 1 root root   8108 2009-01-12 00:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-12 00:40 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-12 00:40 installed-version
-rw-r--r-- 1 root root   8712 2009-01-12 00:40 jfs_stage1_5
-rw-r--r-- 1 root root   4621 2009-01-12 00:41 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-12 00:40 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-12 00:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-12 00:40 stage1
-rw-r--r-- 1 root root 121460 2009-01-12 00:40 stage2
-rw-r--r-- 1 root root   9556 2009-01-12 00:40 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 10  0a d4 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 81 3e 72  04 45 44 74 1d ff 0e 13  |{.....>r.EDt....|
00000060  04 8b 0e 13 04 c1 e1 06  8e c1 b9 00 01 33 f6 33  |.............3.3|
00000070  ff f3 66 a5 c7 06 72 04  45 44 8e c0 bd 00 7c e8  |..f...r.ED....|.|
00000080  21 01 0f 82 bb 00 66 0f  b7 86 16 00 66 d1 e0 66  |!.....f.....f..f|
00000090  0f b7 9e 0e 00 66 03 c3  66 03 86 1c 00 66 89 86  |.....f..f....f..|
000000a0  3e 00 8b 86 11 00 c1 e8  04 89 86 46 00 bb 00 05  |>..........F....|
000000b0  e8 aa 00 0f 82 8a 00 ba  10 00 b9 0b 00 be f2 7d  |...............}|
000000c0  8b fb f3 a6 74 16 83 c3  20 4a 75 ee 66 ff 86 3e  |....t... Ju.f..>|
000000d0  00 ff 8e 46 00 75 d6 be  e1 7d eb 6d 66 0f b7 86  |...F.u...}.mf...|
000000e0  11 00 66 ba 20 00 00 00  66 f7 e2 66 0f b7 8e 0b  |..f. ...f..f....|
000000f0  00 66 03 c1 66 48 66 f7  f1 66 01 86 3e 00 66 8b  |.f..fHf..f..>.f.|
00000100  86 3e 00 66 89 46 fc 66  0f b7 47 1a 8b f8 2d 02  |.>.f.F.f..G...-.|
00000110  00 66 0f b6 9e 0d 00 66  f7 e3 66 01 86 3e 00 bb  |.f.....f..f..>..|
00000120  00 07 c7 86 46 00 04 00  e8 32 00 72 14 81 c3 00  |....F....2.r....|
00000130  02 66 ff 86 3e 00 ff 8e  46 00 75 ec ea 00 02 70  |.f..>...F.u....p|
00000140  00 be d4 7d eb 03 be e1  7d e8 02 00 eb fe ac 3c  |...}....}......<|
00000150  00 74 09 b4 0e bb 07 00  cd 10 eb f2 c3 66 8b 86  |.t...........f..|
00000160  3e 00 66 33 d2 66 0f b7  8e 18 00 66 f7 f1 66 42  |>.f3.f.....f..fB|
00000170  88 96 45 00 66 33 d2 66  0f b7 8e 1a 00 66 f7 f1  |..E.f3.f.....f..|
00000180  88 96 44 00 89 86 42 00  b8 01 02 8b 8e 42 00 c0  |..D...B......B..|
00000190  e5 06 0a ae 45 00 86 e9  8a b6 44 00 8a 96 24 00  |....E.....D...$.|
000001a0  cd 13 c3 80 3e c2 07 06  74 29 b8 01 02 bb 00 06  |....>...t)......|
000001b0  b9 01 00 b6 00 8a 96 24  00 cd 13 72 16 c6 06 c2  |.......$...r....|
000001c0  07 06 b8 01 03 bb 00 06  b9 01 00 b6 00 8a 96 24  |...............$|
000001d0  00 cd 13 c3 44 69 73 6b  20 65 72 72 6f 72 0d 0a  |....Disk error..|
000001e0  00 4d 69 73 73 69 6e 67  20 6c 6f 61 64 65 72 0d  |.Missing loader.|
000001f0  0a 00 49 4f 20 20 20 20  20 20 53 59 53 00 55 aa  |..IO      SYS.U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-12
Since you ran the Super Grub Disk to restore the Windows boot loader in your sda drive, can you boot Windows? If you have Windows XP, it doesn't look like you should be able to, because for one thing your Windows partition is missing its boot.ini file, and also the script couldn't identify that partition (sda2) as a full Windows install. Do you maybe have an older version of Windows?

But about booting Kubuntu, can you change your computer's BIOS to boot the sdb slave drive on start up instead of the sda drive? That would be the most ideal I think because then your drives won't be dependent on each other for booting, but I'm not sure if your BIOS would support it. But whether you can boot the sdb drive or not, how about following these steps from your Live CD to reinstall Grub:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd[COLOR="Red"]X[/COLOR])
grub> quit
```
If your BIOS supports booting your sdb drive, let X=1 in the above setup command, but if not, let X=0; also, please post the output of the above commands before doing "quit". Then reboot, and let me know exactly what happens on start up, and if you get the same Grub error 5. We can work from there if you want.

---

### Post by jimmyboy76453 on 2009-01-12
Once I uninstalled grub, I could boot Windows just fine. It is XP, and it came installed with the computer, if that makes a difference. I don't know about the missing file and stuff. 

I did what you said, and here is the resulting text. I am going to reboot now and I will reply again to let you know what happened. 

     ```
  [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root(hd1,0)

Error 27: Unrecognized command

grub> root (hd1,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by jimmyboy76453 on 2009-01-12
Gave me the same Error 5 message.
I had to run SuperGrubDisk and uninstall grub again to get Windows to boot.

---

### Post by caljohnsmith on 2009-01-12
I think it would be worth mentioning that a Grub error 5 is:
[QUOTE=Official Grub Manual]Error 5: Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.[/QUOTE]
I've looked over the partition table on your sdb drive, and as far as I can tell, I don't see anything wrong with it; I suspect you are getting the Grub error because it sounds like your BIOS is a bit old, and that's sometimes the cause when Grub reports errors don't make logical sense. Or sometimes in rare cases in the forums I've seen where these type of Grub problems are caused by not having the master/slave drives jumpered correctly. Is the Ubuntu drive jumpered for slave or cable-select? You could try changing it to one or the other and see if it makes a difference about booting Ubuntu (you would have to first reinstall Grub to sda again using the previous commands). 

Also, how about trying the following:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
That will install Grub to the MBR (Master Boot Record) of your Ubuntu drive. Then boot your Super Grub Disk, and at the first main menu, press "c" to get the command line, and then do:
```
grub> rootnoverify (hd1)
grub> chainloader +1
grub> boot
```
And let me know exactly what happens. We can work from there. :)

---

### Post by jimmyboy76453 on 2009-01-12
Not sure how to change the jumper, but I typed in what you said in SuperGrubDisk and what I got was the same "Loading Grub, please wait" and then "Error 5."

When my computer loads and the Dell screen appears, it says on it, "BIOS Revision A01", if that means anything to you about how old my BIOS is.

---

### Post by caljohnsmith on 2009-01-12
Can you go into your BIOS and let me know what HDD-related settings you have available? Look for things like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.

---

### Post by jimmyboy76453 on 2009-01-14
I'm not exactly sure if this is what you need, but here is the entire menu that comes up when I hit F2, including some sub-menus if I thought they were relevant. I know a lot of this is useless information. 
> 
System Time
System date
Drive configuration
&#61672;	Primary Master  Hard-disk drive
&#61672;	Primary Slave   Hard-disk drive
&#61672;	Secondary Master  CD-ROM drive
&#61672;	Secondary Slave  CD-ROM drive
&#61672;	IDE Drive UDMA      ON
HDD Sequence
1.	System BIOS boot devices
2.	USB Device (not installed)
Boot Sequence
1.	IDE CD-ROM Device
2.	Hard-disk Drive C:
Memory Information
CPU Information
Integrated Devices (Legacyselect options)
&#61672;	Sound      ON
&#61672;	Network Interface Controller    ON
&#61672;	Mouse Port     ON
&#61672;	USB Emulation     ON
&#61672;	USB Controller      ON
&#61672;	Serial Port     ON
&#61672;	Parallel Port
o	Mode
&#61607;	PS/2 (this was the selected option)
&#61607;	EPP
&#61607;	ECP  (opens another menu called DMA Channel)
•	DMA Channel
o	OFF (this was the selected option)
o	DMA1
o	DMA3
&#61607;	OFF
&#61607;	AT
o	I/O Address
&#61672;	Diskette Interface    
o	OFF (this was the selected option)
o	Auto
o	Read Only
&#61672;	Primary Video Controller
o	Auto (selected)
o	Onboard
&#61672;	Onboard Video Buffer
o	1MB (selected)
o	8MB
Power Management
System Security
Keyboard Numlock    ON
Report Keyboard Errors     REPORT
Auto Power On     DISABLED
Fast Boot   ON
OS Install Mode    OFF
Limit CPUID Value    DISABLED
IDE Hard Drive Acoustics Mode     PERFORMANCE
Sysem Event Log
Asset Tag


---

### Post by caljohnsmith on 2009-01-14
Can you open up your computer and check that your HDDs are jumpered correctly? I just would like to rule that out as a possible cause of your problem, because I've seen in the past where that has been the culprit of strange Grub errors. If you check your HDD documentation, they should have info of how to set the jumper on the drive so you can choose between "master", "slave", or "cable-select". Here is some more info in case it helps:

[http://en.wikipedia.org/wiki/AT_Attachment](http://en.wikipedia.org/wiki/AT_Attachment)
[http://en.wikipedia.org/wiki/Jumper_(computing](http://en.wikipedia.org/wiki/Jumper_(computing))

Let me know how that goes and we can work from there.

---

### Post by jimmyboy76453 on 2009-01-14
It appears my master drive was jumpered as cable select and my slave drive as slave. I re-jumpered the master drive as master, and re-installed GRUB to hd0, but it gave me the same message again. Is there something else I should do, like re-installing Kubuntu or something?

---

### Post by caljohnsmith on 2009-01-14
> **jimmyboy76453 said:**
> It appears my master drive was jumpered as cable select and my slave drive as slave. I re-jumpered the master drive as master, and re-installed GRUB to hd0, but it gave me the same message again. Is there something else I should do, like re-installing Kubuntu or something?
Unfortunately I don't think it is likely that reinstalling Kubuntu will help at all, because Kubuntu will just reinstall Grub in the same way it did last time, which is is essentially the same way you have been reinstalling Grub. One more easy thing you could try is to change the "IDE Drive UDMA ON" setting in your BIOS to off (if it will let you). Let me know if that makes any difference about the Grub error you get on start up.

---

### Post by jimmyboy76453 on 2009-01-14
did what you said, and this time I got Error 25.

---

### Post by caljohnsmith on 2009-01-14
OK, since that gave a Grub error 25, if you haven't done it all ready, I would go ahead and change the "IDE Drive UDMA" setting back to "on". I'm not sure what else to suggest, but here's one more thing we can try that is a bit of a long shot yet might make a difference:
```
sudo grub
grub> root (hd1,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
That installs Grub to the MBR of your Windows drive again, but it omits Grub's stage1.5 file; instead Grub in the MBR points directly to the stage2 file on your Kubuntu drive. Sometimes that trick has worked to circumvent really strange and illogical Grub errors, so it couldn't hurt to try in your case. Let me know what happens.

---

### Post by jimmyboy76453 on 2009-01-14
No, that didn't work. I got this message: "Warning: the option 'd' was not used, but the stage 1 will be installed on a different drive than the drive where the stage 2 resides."

When I rebooted, it said, "GRUB GEOM Error"

Sad, but I'm going to give up on Linux for now. After uninstalling GRUB (again) through SuperGrubDisk, I can get into Windows ok, so all I need to figure out is how to wipe my entire slave drive and start fresh without screwing up my master drive.

---

### Post by caljohnsmith on 2009-01-14
My mistake, I see I got the Grub command syntax wrong. But I can totally understand and respect that you've decided not to pursue Ubuntu for now, considering that Ubuntu does not seem to work to well with your hardware so far. Cheers and best wishes.

---

