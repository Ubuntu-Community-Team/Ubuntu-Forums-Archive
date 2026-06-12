---
title: "xp boot problem restore windows mbr but not installed to root partition!"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by paulc86 on 2009-01-20
Hi everyone,

Thanks for looking

I have a problem as follows, I think I might have made life difficult for myself hear...

Ive just reformatted my entire system, including repartitioning to look like this..

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+  83  Linux
/dev/sda2            6375       30400   192988845    f  W95 Ext'd (LBA)
/dev/sda5            6375        6884     4096543+  82  Linux swap / Solaris
/dev/sda6            6885        9434    20482843+   7  HPFS/NTFS
/dev/sda7            9435       30400   168409363+   7  HPFS/NTFS

with windows xp being installed on /dev/sda6 and buntu on sda1

I thought to do this because ubuntu is my main op sys now but need xp for one a special bit of kit that will not work with ubuntu:(

anyway XP is not in the grub boot menu and I dont fancy using the XP fixmbr command as I have a sneaky feeling that it will kill my partitions.

what i was thinking was that I need to somehow restore a mbr to sda6 and point grub to that....
but thats as far as ive got so far..

any help would really be aprichiated ive already searched high and low for the answer but I really dont want to mess this up as I am supper happy with my current installs!

---

### Post by caljohnsmith on 2009-01-20
Did you actually install XP to sda6, or did you move it there? XP won't install to a logical partition like sda6 unless there is a primary NTFS/FAT partition available where Windows can put its boot files, but you don't seem to have any. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot XP.

---

### Post by paulc86 on 2009-01-21
Thanks, what I did was to install XP first, it formated the first partition as NTFS and installed in the third. After the XP install I then reformatted the first as ext3 for ubuntu.

hear is the output your requested, I also have USB external disk plugged in so this may affect the output?

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda7 starts at sector 151557273. Grub0.97 in the file 
                       /MBR-backup looks at sector 1 of the same hard drive 
                       for the stage2 file and on the same partition for 
                       /boot/grub/stage2 /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1871ca1e

/dev/sda1     *           63  102,398,309  102,398,247  83 Linux
/dev/sda2        102,398,310  488,375,999  385,977,690   f W95 Ext'd (LBA)
/dev/sda5        102,398,373  110,591,459    8,193,087  82 Linux swap / Solaris
/dev/sda6        110,591,523  151,557,209   40,965,687   7 HPFS/NTFS
/dev/sda7        151,557,273  488,375,999  336,818,727   7 HPFS/NTFS

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

/dev/sdb1     *           63  976,768,064  976,768,002   7 HPFS/NTFS

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="843dde69-ffbd-49d5-8354-fa9e649a7709" TYPE="ext3" 
/dev/sda5: UUID="c16a3f6d-666d-45ff-a685-b3385b05ad36" TYPE="swap" 
/dev/sda7: UUID="1E9CB70F9CB6E087" LABEL="store" TYPE="ntfs" 
/dev/sdb1: UUID="960892CA0892A92F" LABEL="FreeAgent Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda7 on /media/store type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)

=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=843dde69-ffbd-49d5-8354-fa9e649a7709 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=843dde69-ffbd-49d5-8354-fa9e649a7709

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
uuid		843dde69-ffbd-49d5-8354-fa9e649a7709
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=843dde69-ffbd-49d5-8354-fa9e649a7709 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		843dde69-ffbd-49d5-8354-fa9e649a7709
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=843dde69-ffbd-49d5-8354-fa9e649a7709 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		843dde69-ffbd-49d5-8354-fa9e649a7709
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd0,6)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=843dde69-ffbd-49d5-8354-fa9e649a7709 /               ext3    errors=remount-ro 0       1
# /dev/sda7
UUID=1E9CB70F9CB6E087 /media/store    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=2848BA5148BA1E0E /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=c16a3f6d-666d-45ff-a685-b3385b05ad36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#VBox USB Support
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

================================== sda1/boot: ==================================

total 12808
drwxr-xr-x  4 root root    4096 2009-01-20 23:20 .
drwxr-xr-x 21 root root    4096 2009-01-18 12:25 ..
-rw-r--r--  1 root root  503560 2008-10-24 08:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 08:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-20 23:21 extlinux
drwxr-xr-x  3 root root    4096 2009-01-20 23:24 grub
-rw-r--r--  1 root root 8641755 2009-01-17 21:07 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 08:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 08:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 08:55 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 228
drwxr-xr-x 3 root root   4096 2009-01-20 23:24 .
drwxr-xr-x 4 root root   4096 2009-01-20 23:20 ..
-rw-r--r-- 1 root root    197 2009-01-17 21:07 default
-rw-r--r-- 1 root root     15 2009-01-17 21:07 device.map
-rw-r--r-- 1 root root   8108 2009-01-17 21:07 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-17 21:07 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-17 21:07 installed-version
-rw-r--r-- 1 root root   8712 2009-01-17 21:07 jfs_stage1_5
-rw-r--r-- 1 root root   4376 2009-01-20 23:24 menu.lst
-rw-r--r-- 1 root root   4376 2009-01-20 23:24 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-17 21:07 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-17 21:07 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2009-01-20 21:29 splashimages
-rw-r--r-- 1 root root    512 2009-01-17 21:07 stage1
-rw-r--r-- 1 root root 121460 2009-01-17 21:07 stage2
-rw-r--r-- 1 root root   9556 2009-01-17 21:07 xfs_stage1_5

=================== sda1: Location  of files loaded by Grub: ===================


  50.3GB: boot/grub/menu.lst
  50.3GB: boot/grub/stage2
  50.4GB: boot/initrd.img-2.6.27-7-generic
  50.3GB: boot/vmlinuz-2.6.27-7-generic
  50.4GB: initrd.img
  50.3GB: vmlinuz

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on sda6

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  44 52 20 69 73 20 63 6f  |.....,DcDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sda6: unknown volume type

```

I think things may be in a bit of a mess!

Would it be an option to move my ubuntu install to another partition and reinstall XP? Or is there a solution to this mess?

Thanks

---

### Post by caljohnsmith on 2009-01-21
For some reason your sda6 Windows partition was not even mountable. Given that and also that XP is a fresh install, I think you would be better off simply reinstalling XP at this point. As I mentioned though, since you don't have any primary NTFS/FAT partitions, Windows won't let you install itself to sda6 again. I think your best bet would be to delete the sda5 swap partition and also the sda6 Windows partition, recreate the swap partition so that it comes right before the sda7 partition, and resize the sda2 extended partition so that it begins right at the beginning of the swap file. Then you should have 40 GB of free space after sda1 and before sda2 where you can create a primary partition for Windows. If all goes well and you install Windows successfully, you'll need to reinstall Grub afterwards:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Also, when you boot into Ubuntu, you'll probably notice that the Ubuntu splash screen is missing; that's because you'll need to tell Ubuntu to use your new swap partition. So once you boot into Ubuntu do:
```
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/[COLOR="Blue"]sdaX[/COLOR]
```
And replace "sdaX" with the new swap partition. Then reboot, see if you have the splash screen back, and when you get into Ubuntu please post:
```
sudo blkid -c /dev/null
sudo fdisk -lu
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
free
```
So I can check everything went OK. We can work from there if you want.

---

### Post by paulc86 on 2009-01-22
Thanks very much thats seamed to have sorted things perfectly, and for better or worse I can now boot into XP again!

Hear is the output you requested

sudo blkid -c /dev/null
```

/dev/sda1: UUID="843dde69-ffbd-49d5-8354-fa9e649a7709" TYPE="ext3" 
/dev/sda2: UUID="4FB00E52184DBE51" TYPE="ntfs" 
/dev/sda4: UUID="1E9CB70F9CB6E087" LABEL="store" TYPE="ntfs" 
/dev/sda5: UUID="c16a3f6d-666d-45ff-a685-b3385b05ad36" TYPE="swap" 

```

sudo fdisk -lu
```

omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1871ca1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   102398309    51199123+  83  Linux
/dev/sda2   *   102398310   143347994    20474842+   7  HPFS/NTFS
/dev/sda3       143347995   488375999   172514002+   f  W95 Ext'd (LBA)
/dev/sda4       151557210   488375999   168409395    7  HPFS/NTFS
/dev/sda5       143364123   151557209     4096543+  82  Linux swap / Solaris

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=843dde69-ffbd-49d5-8354-fa9e649a7709 /               ext3    errors=remount-ro 0       1
# /dev/sda7
UUID=1E9CB70F9CB6E087 /media/store    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=2848BA5148BA1E0E /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=c16a3f6d-666d-45ff-a685-b3385b05ad36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#VBox USB Support
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

cat /etc/initramfs-tools/conf.d/resume
```

RESUME=UUID=c16a3f6d-666d-45ff-a685-b3385b05ad36

```

free
```
             total       used       free     shared    buffers     cached
Mem:       4054484     910536    3143948          0      25292     347796
-/+ buffers/cache:     537448    3517036
Swap:      4096532          0    4096532
```

All seams to be OK but let me know if you think there are any problems, thanks again.

P

---

### Post by caljohnsmith on 2009-01-22
That looks great, it looks like you're all set; cheers and enjoy Windows and Ubuntu. :)

---

### Post by paulc86 on 2009-01-23
Yeah thanks again. Enjoy Windows! not sure about that apart from the one application (Serato Scratch Live).

Cheers,

P

---

