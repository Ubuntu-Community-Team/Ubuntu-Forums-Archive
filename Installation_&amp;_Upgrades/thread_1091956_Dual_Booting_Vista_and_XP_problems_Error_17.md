---
title: "Dual Booting Vista and XP problems: Error 17"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by JoeJJohnsonII on 2009-03-09
Hello all,
     I've been trying to get ubuntu working on my desktop for some time now. Whenever I install it, I get an error from the grub loader: error 17. After messing with it for a couple of minutes, I pulled out my vista dvd and restored the vista boot loader so I could still use my comp. I've been reading a lot of posts lately looking for a solution, but havent been able to come up with anything on my own. Heres some logs that other people have been asked to provide before.

BootInfo script results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-9B0468F8F0AB380958FFBD66FC8D9CCD.mbr is 
                       trying to chain load sector #418011300 on boot drive 
                       #2 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #426011670 on boot drive #2
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 579939350 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1465143295 sectors, but according to the info from 
                       fdisk, it has 1465147057 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       976769023 sectors, but according to the info from 
                       fdisk, it has 976782082 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01e666c9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   418,008,414   418,008,352   7 HPFS/NTFS
/dev/sda2         418,011,300   426,011,669     8,000,370  82 Linux swap / Solaris
/dev/sda3         426,011,670   586,067,264   160,055,595  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48db48da

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,147,119 1,465,147,057  42 SFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88ad1642

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   976,784,129   976,782,082   7 HPFS/NTFS

/dev/sdc1 ends after the last sector of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="682013D92013AD56" TYPE="ntfs" 
/dev/sda2: UUID="fce42f53-1c3e-4234-b480-84b9cff330b9" TYPE="swap" 
/dev/sda3: UUID="46ff47b0-edaa-4367-abea-3a48d39fab28" TYPE="ext3" 
/dev/sdb1: UUID="7A94269494265345" TYPE="ntfs" 
/dev/sdc1: UUID="9C120F58120F3734" TYPE="ntfs" 
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
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="WinBandit XP Lite v1.7" /noexecute=optin /fastdetect /kernel=singkrnl.exe

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=46ff47b0-edaa-4367-abea-3a48d39fab28 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=46ff47b0-edaa-4367-abea-3a48d39fab28

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
uuid		46ff47b0-edaa-4367-abea-3a48d39fab28
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=46ff47b0-edaa-4367-abea-3a48d39fab28 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		46ff47b0-edaa-4367-abea-3a48d39fab28
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=46ff47b0-edaa-4367-abea-3a48d39fab28 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		46ff47b0-edaa-4367-abea-3a48d39fab28
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=46ff47b0-edaa-4367-abea-3a48d39fab28 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=fce42f53-1c3e-4234-b480-84b9cff330b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 296.9GB: boot/grub/menu.lst
 296.9GB: boot/grub/stage2
 296.7GB: boot/initrd.img-2.6.27-7-generic
 296.7GB: boot/vmlinuz-2.6.27-7-generic
 296.7GB: initrd.img
 296.7GB: vmlinuz
```

fdisk results:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01e666c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26020   209004176    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           26021       26518     4000185   82  Linux swap / Solaris
/dev/sda3           26519       36481    80027797+  83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48db48da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732573528+  42  SFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88ad1642

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488391041    7  HPFS/NTFS

```

I found another post that had a similar problem, but I couldnt complete all the steps he posted: [Link to other Post]("http://ubuntuforums.org/showthread.php?t=1036463&referrerid=787315")

 ```
      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

grub> setup (hd0,0)

Error 17: Cannot mount selected partition

grub> 

```

Thanks for any help you guys can give me.

-JoeJJohnsonII

---

### Post by jackhynes on 2009-03-09
I had this problem a while ago and eventually found that my BIOS could not cope with the size of the new hard drive I had installed. I had installed GRUB + OS outside of the size limits and therefore it could not read either one.

---

### Post by theozzlives on 2009-03-09
> **jackhynes said:**
> I had this problem a while ago and eventually found that my BIOS could not cope with the size of the new hard drive I had installed. I had installed GRUB + OS outside of the size limits and therefore it could not read either one.

When I had that problem, I partitioned off my Ubuntu and it worked fine.

---

### Post by JoeJJohnsonII on 2009-03-09
> **jackhynes said:**
> I had this problem a while ago and eventually found that my BIOS could not cope with the size of the new hard drive I had installed. I had installed GRUB + OS outside of the size limits and therefore it could not read either one.

So how would I check to see if this is happening? Would this still happen if the Linux partition is installed at the end of a HD?

---

### Post by meierfra. on 2009-03-09
The grub stage1 file in your ubuntu boot sector seems to be correctly configured. So lets see what happens when you set the boot flag to the Ubuntu partition:

```
sudo grub
```
and at the grub prompt

```
root (hd0,2)
makeactive
quit
```

(if this does not work, you can set the boot flag back to the Vista partition by using "root (hd0,0)" in place of "root (hd0,2)".

---

### Post by JoeJJohnsonII on 2009-03-10
> **meierfra. said:**
> The grub stage1 file in your ubuntu boot sector seems to be correctly configured. So lets see what happens when you set the boot flag to the Ubuntu partition:

```
sudo grub
```
and at the grub prompt

```
root (hd0,2)
makeactive
quit
```

(if this does not work, you can set the boot flag back to the Vista partition by using "root (hd0,0)" in place of "root (hd0,2)".

It read the GRUB loader but it still pops up with "error 17: File not found". I didn't have to switch it back to the vista partition though because it read the vista entry and worked correctly when I selected it from the menu.

---

### Post by meierfra. on 2009-03-10
Strange.  Since the grub menu appears, it means that grub is able to find "menu.lst" but is not able to find the kernel.  According to the results from the boot info script

> 296.9GB: boot/grub/menu.lst
 296.9GB: boot/grub/stage2
 296.7GB: boot/initrd.img-2.6.27-7-generic
 296.7GB: boot/vmlinuz-2.6.27-7-generic


your kernel is not missing and is even slightly closer to the beginning of the hard drive than menu.lst.  So I doubt that your  problem has anything to do with the size limits of your bios.  But it also means that I have no good idea what the problem could be.

This might not  cure  your problems, but lets see what happens if you replace the  UUID's in the grub menu  by  "(hd0,2)":

At the grub menu during boot up, select ubuntu but do not press "enter". Instead press "e". At the new screen  press "e" again.

Change 

"uuid 46ff47b0-edaa-4367-abea-3a48d39fab28" 

to 

"root (hd0,2)"

Press "enter" and then "b" to  try to boot into Ubuntu.

If this works, you have to make these changes permanent by editing menu.lst:

Open a terminal  and type 

```
gksudo gedit /boot/grub/menu.lst
```

to open  the file "menu.lst".

Change 

# groot=46ff47b0-edaa-4367-abea-3a48d39fab28

to

# groot=(hd0,2)


Save the file. Then in the terminal

```
sudo update-grub
```

---

