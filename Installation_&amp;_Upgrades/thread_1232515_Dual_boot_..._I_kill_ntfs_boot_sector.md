---
title: "Dual boot ... I kill ntfs boot sector"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by estebarb on 2009-08-05
I have installed Ubuntu 9.04 in a tri-boot with win7, xp and ubuntu, everyone with their own hard disk. Before Ubuntu I have suse with grub, the tri boot and everything ok.
When I install ubuntu I the grub was installed in the mbr so I can't start xp, but win7 is ok and I can see both hard disks with ubuntu.
Right now my problem is that I follow the instruccions to restore xp (with ms-sys) and now Ubuntu don't recognize my xp partition (the biggest one, with 500 gb), and I can't load xp nor seven (but I can still see with ubuntu).
Please help me to recover the xp partition, or at least see it from ubuntu again. Format is not an option because I have very important information there :S.
I already tried hirens boot cd and with one @active *** tools I can see the files when reading from partition table but not when reading from boot sector. Maybe I need a way to restore the boot sector.
Thanks! and sorry for my english, I must improve them :p.

---

### Post by presence1960 on 2009-08-05
Boot into Ubuntu or from the Live CD. When the desktop loads download to the desktop [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/"). Then open a termimal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. paste the contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. This info will show us your partition table, boot info & other useful info about your setup.

---

### Post by estebarb on 2009-08-05
Thanks! I have recover the boot sector of the NTFS partition, with TestDisk ([http://www.cgsecurity.org/](http://www.cgsecurity.org/) and is GPLed :p), so I can see again my files in Ubuntu :D. Right now I'm figure how to boot xp or win7, but I'm scary to crash again the partitions :S. I'm going to post any update of the situation and the solution (if I find it :p). By now, TestDisk was a step in the proper direction :D :D :D.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 60223039 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xb7e61057

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x00037d34

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,204,419    78,204,357  83 Linux
/dev/sdb2          78,204,420   312,576,704   234,372,285   5 Extended
/dev/sdb5          78,204,483    89,915,804    11,711,322  82 Linux swap / Solaris
/dev/sdb6          89,915,868   312,576,704   222,660,837  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xb7e61057

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    78,161,919    78,159,872   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BCBC46E4BC469932" TYPE="ntfs" 
/dev/sdb1: UUID="8c4aa09d-ddca-4709-b980-c1417a959773" TYPE="ext3" 
/dev/sdb5: UUID="c9d686e6-46bf-4410-8e45-801a8d4ea917" TYPE="swap" 
/dev/sdb6: UUID="66c44b3c-c900-4930-9cc4-12be5f667f15" TYPE="ext3" 
/dev/sdc1: UUID="2824CAA824CA77F8" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/esteban/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=esteban)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTOUT 

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
# kopt=root=UUID=8c4aa09d-ddca-4709-b980-c1417a959773 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c4aa09d-ddca-4709-b980-c1417a959773

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        8c4aa09d-ddca-4709-b980-c1417a959773
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8c4aa09d-ddca-4709-b980-c1417a959773 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        8c4aa09d-ddca-4709-b980-c1417a959773
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8c4aa09d-ddca-4709-b980-c1417a959773 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8c4aa09d-ddca-4709-b980-c1417a959773
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8c4aa09d-ddca-4709-b980-c1417a959773 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8c4aa09d-ddca-4709-b980-c1417a959773
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8c4aa09d-ddca-4709-b980-c1417a959773 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8c4aa09d-ddca-4709-b980-c1417a959773
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
chainloader    +1

title        Windows XP (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=8c4aa09d-ddca-4709-b980-c1417a959773 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=66c44b3c-c900-4930-9cc4-12be5f667f15 /home           ext3    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=c9d686e6-46bf-4410-8e45-801a8d4ea917 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.7GB: boot/grub/menu.lst
  30.8GB: boot/grub/stage2
  30.8GB: boot/initrd.img-2.6.28-11-generic
  30.7GB: boot/initrd.img-2.6.28-14-generic
  30.7GB: boot/vmlinuz-2.6.28-11-generic
  30.8GB: boot/vmlinuz-2.6.28-14-generic
  30.7GB: initrd.img
  30.8GB: initrd.img.old
  30.8GB: vmlinuz
  30.7GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-08-05
I need one other piece of information: Boot your machine and report back here the boot order of your hard disks in BIOS. WE already know sdb is booting first because GRUB is installed to the MBR of sdb and GRUB does take over when you boot. I need the exact order of your hard disk boot in BIOS so I can give you the correct settings for windows.

---

### Post by presence1960 on 2009-08-05
let's wing it instead! I have to go to bed soon.

try this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista (loader)
rootnoverify    (hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

title           Windows XP (loader)
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

or 

```
This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista (loader)
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

title           Windows XP (loader)
rootnoverify    (hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

I am assuming here your GRUB menu comes up when you boot. If so that means sdb boots first because GRUB is installed to MBR of sdb. One of those two options should do the trick depending on your sda & sdc boot order in BIOS. You need map lines when windows partition is not located on the hard disk which boots first. Windows needs to think it is on the first boot disk and the map lines "trick" windows into believing it is so.

---

### Post by estebarb on 2009-08-05
Hi!
My first disk is the one of 16GB with ubuntu and GRUB
Next one of 40GB with win7
and last, the XP and the windows bootloader of win7 and XP. As always Microsoft install their things where they want... :|
I try to boot directly from the disks, but it don't work. I'm going to try your GRUB trick :p.

and yes, I also have to sleep, but first... homeworks....... :( I don't want to do that summary!!! :p

---

### Post by estebarb on 2009-08-06
OK, I don't want to do my homework :p and instead of that I try the GRUB tricks.
It don't work in the sense XP or win7 boot, but it loads the win7 bootloader (with the xp and 7 options) and then fails with a so explicative c000000e error (oh Microsoft and their undocumented errors...)
On the other hand, when that faulty windows loader loads and next I start Ubuntu, at the beggining appears a doing routine check of file system (sdb1, or the first partition of the first hard disk in boot order). That means that the windows loader touches ext3 partitions? :s Very strange...

---

### Post by presence1960 on 2009-08-06
You should get a choice between XP & win 7 with the windows bootloader. Unfortunately that is how windows works when you have more than one version of windows installed.

That check has nothing to do with windows touching your Ubuntu partitions. That is a routine check that is run every so many times you boot your machine.

Unfortunately I can't help you with that error. You are going to have to find someone who really knows Microsoft error codes. Your machine is set to boot both windows installations now at least, so your GRUB is set to go. Now you have a windows problem.

---

### Post by estebarb on 2009-08-07
OK, thanks! This is a very rare problem, but I'm sure that is the windows bootloader that produces the FS check. As every problem at Windows I know how to solve it: reinstalling, so I'm going to do that. Althougth I must reinstall Windows, the problem was partially solved, because the boot sector can be restored :D and I can do the backup, so I'm doing that (hey! Ubuntu is faster than other diestros coping files from and to NTFS... an interesting fact :p), I'm going to reinstall later, but I'll detach the Ubuntu disk... I want to protect the penguin :D.

---

