---
title: "Grub Error 15: File not Found Error - After Installation of openSUSE"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Habboblob on 2009-04-10
I have firstly create 1 partition that took up half of my Harddisk and installed Ubuntu onto it. I then decided to give openSUSE a try and installed it onto the other half of the harddisk which was not in use. All went well, any I booted up openSUSE succussfully, but when I choose to boot up Ubuntu, it comes up with the error 15: File not found.

Right now I am currently using openSUSE. I like to occassionally switch operation systems. If this is not possible, and I am only possible to keep 1 operation system please tell me, as I have seen my friend have 2 operating systems, and thought that this could be possible for myself also. Anyways, I hope to see your feedback.:p

I have also tried looking at other thread but this has not helped me in anyway, please also give me a explanation as I am a Linux Noob.

---

### Post by Habboblob on 2009-04-11
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

I have also gotten the Grub Error 15: File not found error and have the result log for you to see.

[http://pastebin.com/f72795fc1](http://pastebin.com/f72795fc1)

Also, if you could, I would like it if you could post the solution onto my thread so that when other people see it they can also find it out.
```
/yes
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 34107775 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2abe2abe

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,302,559    29,302,497  83 Linux
/dev/sda2    *     29,302,560    58,605,119    29,302,560   f W95 Ext d (LBA)
/dev/sda5          29,302,623    30,844,799     1,542,177  82 Linux swap / Solaris
/dev/sda6          30,844,863    42,459,794    11,614,932  83 Linux
/dev/sda7          42,459,858    58,605,119    16,145,262  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="aa4e4700-e20d-4f83-b488-c954c4a05b43" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="5ae01f1c-fa97-49ca-9709-2e270bce099c" TYPE="swap" 
/dev/sda6: UUID="ab9e619c-fb92-458e-aee5-417116989510" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="f91f8392-1168-464d-8699-419b9932e155" SEC_TYPE="ext2" TYPE="ext3" 
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
# kopt=root=UUID=aa4e4700-e20d-4f83-b488-c954c4a05b43 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aa4e4700-e20d-4f83-b488-c954c4a05b43

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
uuid		aa4e4700-e20d-4f83-b488-c954c4a05b43
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=aa4e4700-e20d-4f83-b488-c954c4a05b43 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		aa4e4700-e20d-4f83-b488-c954c4a05b43
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=aa4e4700-e20d-4f83-b488-c954c4a05b43 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		aa4e4700-e20d-4f83-b488-c954c4a05b43
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=aa4e4700-e20d-4f83-b488-c954c4a05b43 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		aa4e4700-e20d-4f83-b488-c954c4a05b43
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=aa4e4700-e20d-4f83-b488-c954c4a05b43 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		aa4e4700-e20d-4f83-b488-c954c4a05b43
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa4e4700-e20d-4f83-b488-c954c4a05b43 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  11.4GB: boot/grub/menu.lst
  11.4GB: boot/grub/stage2
  11.4GB: boot/initrd.img-2.6.27-11-generic
  11.5GB: boot/initrd.img-2.6.27-7-generic
  11.5GB: boot/vmlinuz-2.6.27-11-generic
  11.5GB: boot/vmlinuz-2.6.27-7-generic
  11.4GB: initrd.img
  11.5GB: initrd.img.old
  11.5GB: vmlinuz
  11.5GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sat Apr 11 02:41:43 EST 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-HTS424030M9AT00_MPAA42QBJB1WUB-part6 resume=/dev/disk/by-id/ata-HTS424030M9AT00_MPAA42QBJB1WUB-part5 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.27.7-9-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)###
title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-HTS424030M9AT00_MPAA42QBJB1WUB-part6 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.27.7-9-default

=============================== sda6/etc/fstab: ===============================

/dev/disk/by-id/ata-HTS424030M9AT00_MPAA42QBJB1WUB-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-HTS424030M9AT00_MPAA42QBJB1WUB-part6 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-HTS424030M9AT00_MPAA42QBJB1WUB-part7 /home                ext3       acl,user_xattr        1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda6: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/menu.lst
  17.4GB: boot/grub/stage2
  17.4GB: boot/initrd
  17.4GB: boot/initrd-2.6.27.7-9-default
  17.4GB: boot/vmlinuz
  17.4GB: boot/vmlinuz-2.6.27.7-9-default
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  31 c0 8e d0 bc 00 7c 8e  c0 8e d8 bf 1e 06 be 1e  |1.....|.........|
00000010  7c 50 57 b9 e2 01 f3 a4  b9 00 02 f3 ab cb 80 fa  ||PW.............|
00000020  8f 7e 02 b2 80 52 52 bb  94 07 8d af 2a 00 8a 46  |.~...RR.....*..F|
00000030  04 66 8b 7e 08 66 03 3e  b3 06 84 c0 74 0b 80 7e  |.f.~.f.>....t..~|
00000040  00 80 75 05 66 89 3e 84  0b 83 c5 10 83 c3 09 80  |..u.f.>.........|
00000050  fb b8 75 da b8 e1 00 c1  e0 02 89 c6 66 8b ac 00  |..u.........f...|
00000060  08 66 85 ed 75 19 b8 c5  06 be bb 06 e8 a5 00 89  |.f..u...........|
00000070  c6 e8 9a 00 5a 31 c0 cd  13 cd 18 fb f4 eb fc 66  |....Z1.........f|
00000080  89 2e b3 06 be ab 06 b4  42 5a 52 cd 13 b8 d9 06  |........BZR.....|
00000090  72 d7 a0 00 7c 84 c0 74  03 a1 fe 7d 3d 55 aa b8  |r...|..t...}=U..|
000000a0  e9 06 75 c5 66 89 ee 5a  e9 55 75 10 00 01 00 00  |..u.f..Z.Uu.....|
000000b0  7c 00 00 00 00 00 00 00  00 00 00 45 72 72 6f 72  ||..........Error|
000000c0  20 00 0d 0a 00 4e 6f 20  61 63 74 69 76 65 20 70  | ....No active p|
000000d0  61 72 74 69 74 69 6f 6e  00 44 69 73 6b 20 72 65  |artition.Disk re|
000000e0  61 64 20 65 72 72 6f 72  00 4e 6f 20 6f 70 65 72  |ad error.No oper|
000000f0  61 74 69 6e 67 20 73 79  73 74 65 6d 00 49 6e 76  |ating system.Inv|
00000100  61 6c 69 64 20 43 48 53  20 72 65 61 64 00 e8 03  |alid CHS read...|
00000110  00 be c2 06 60 ac b4 0e  bb 01 00 cd 10 ac 84 c0  |....`...........|
00000120  75 f4 61 c3 00 00 00 00  00 00 00 00 00 00 00 00  |u.a.............|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  1c 80 b6 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  be 2a be 2a 00 00 00 01  |.........*.*....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 e1 1e bf 01 80 fe  |......?.........|
000001d0  ff ff 0f fe ff ff 20 1f  bf 01 20 1f bf 01 00 00  |...... ... .....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by meierfra. on 2009-04-11
The Suse Grub does not understand "UUID's". So you have to use "chainloader" instead of "configfile":

Boot into Suse and open a terminal and install grub to the boot sector of the Ubuntu partition:

```
sudo grub
```
and at the grub prompt:

```
root (hd0,0)
setup (hd0,0)
quit
```

You also need to edit the Suse menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
(If you don't have "gedit"  try "kate" instead of "gedit")

Then change 

title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

to

title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    chainloader +1


Save the file,  and see whether you can boot into Ubuntu.

---

### Post by Habboblob on 2009-04-13
> **meierfra. said:**
> The Suse Grub does not understand "UUID's". So you have to use "chainloader" instead of "configfile":

Boot into Suse and open a terminal and install grub to the boot sector of the Ubuntu partition:

```
sudo grub
```
and at the grub prompt:

```
root (hd0,0)
setup (hd0,0)
quit
```

You also need to edit the Suse menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
(If you don't have "gedit"  try "kate" instead of "gedit")

Then change 

title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

to

title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    chainloader +1


Save the file,  and see whether you can boot into Ubuntu.

:-o :biggrin: :grin:
Thank you so much! for the feedback and yes, and can now boot into both Ubuntu (which I prefer =D) and openSUSE.
):P
Also, could someone please close this thread.

:popcorn:

---

### Post by meierfra. on 2009-04-13
> yes, and can now boot into both Ubuntu (which I prefer =D) and openSUSE.

Great. Have fun with all your OSs.

---

