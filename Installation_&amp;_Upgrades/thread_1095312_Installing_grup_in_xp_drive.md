---
title: "Installing grup in xp drive"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by elliotn on 2009-03-13
When I installed Ubuntu 8.4 grub was installed in the hard drive with XP not in the second hard drive that had Ubuntu. Now is it possible to do that without erasing 8.10 on the second drive. .,well I mean I have 2 hard drives, one with Ubuntu 8.10and the other with XP, so what I want to do is install grub in the drive that has Xp so I can dual boot both, note I dont want to edit grup and add xp as I have failed

---

### Post by meierfra. on 2009-03-13
In order to get a clearer picture of your setup, I suggest to boot into Ubuntu and download the Boot Info Script to your desktop:

[B][https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")
[/B]
Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by elliotn on 2009-03-13
ok Here is what I got.............................
```


 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 32. But according to the info from fdisk, 
                       sdd1 starts at sector 375.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde1da92c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,624,229    37,624,167  83 Linux
/dev/sda2          37,624,230    39,102,209     1,477,980   5 Extended
/dev/sda5          37,624,293    39,102,209     1,477,917  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

```

---

### Post by meierfra. on 2009-03-13
Could you post the whole "RESULTS.txt". It seems the second half got cut off.

---

### Post by meierfra. on 2009-03-13
> so what I want to do is install grub in the drive that has Xp so I can dual boot both, 

???  That would make dual booting any easier.  I actually recommend keeping grub on the Ubuntu partition,  to keep the two OS's independent from each other.

But maybe I'm misunderstanding. Do you want to add Ubuntu to the Windows boot loader?

> I dont want to edit grup and add xp as I have failed 

If you want, I can show you how to edit "menu.lst" correctly.


Also right now you should be able to boot from Ubuntu and XP just by switching the boot order in the bios

---

### Post by elliotn on 2009-03-13
ok Show me how must I edit Grub. btw here is the rest of the txt
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 32. But according to the info from fdisk, 
                       sdd1 starts at sector 375.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde1da92c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,624,229    37,624,167  83 Linux
/dev/sda2          37,624,230    39,102,209     1,477,980   5 Extended
/dev/sda5          37,624,293    39,102,209     1,477,917  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbcacbca

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,220,484    78,220,422   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 27 MB, 27249152 bytes
1 heads, 11 sectors/track, 4838 cylinders, total 53221 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *              7        53,127        53,121   4 FAT16 <32M


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2045 MB, 2045771776 bytes
128 heads, 32 sectors/track, 975 cylinders, total 3995648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *            375     3,995,647     3,995,273   6 FAT16

/dev/sdd1 ends after the last cylinder of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="78d4e77b-ae5f-4f16-b92b-f54aeda58e55" TYPE="ext3" 
/dev/sda5: UUID="653dbc10-b8e5-4fdc-9d26-3650fedb4618" TYPE="swap" 
/dev/sdb1: UUID="3294781C9477E0B1" TYPE="ntfs" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="PHONE" UUID="49BA-D3FE" TYPE="vfat" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="PHONE CARD" UUID="49BA-D3F1" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
capifs on /dev/capi type capifs (rw,mode=0666)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/elliotn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=elliotn)
/dev/sdd1 on /media/PHONE CARD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/PHONE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
# kopt=root=UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=78d4e77b-ae5f-4f16-b92b-f54aeda58e55

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
uuid		78d4e77b-ae5f-4f16-b92b-f54aeda58e55
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		78d4e77b-ae5f-4f16-b92b-f54aeda58e55
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		78d4e77b-ae5f-4f16-b92b-f54aeda58e55
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb
title		Microsoft Windows XP Professional
root		(hd1.0)
savedefault
makeactive
chainloader	+1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=653dbc10-b8e5-4fdc-9d26-3650fedb4618 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  15.4GB: boot/grub/menu.lst
  15.4GB: boot/grub/stage2
  15.4GB: boot/initrd.img-2.6.27-7-generic
  15.3GB: boot/vmlinuz-2.6.27-7-generic
  15.4GB: initrd.img
  15.3GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=X971AD

```

---

### Post by meierfra. on 2009-03-13
Open "menu.lst" via

> gksudo gedit /boot/grub/menu.lst

and add this three items at the end of the file:

title Microsoft Windows XP Professional (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1



title Microsoft Windows XP Professional (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

title Microsoft Windows XP Professional (hd3)
rootnoverify (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader	+1


Reboot and try all three entries. If one of them works, you can deleted all the other from menu.lst. If none of them worked, please report any error messages you got.

---

### Post by meierfra. on 2009-03-13
I just fixed a couple of typos in the second item.

---

### Post by elliotn on 2009-03-13
Error 11: unrecognized device string

Press any key to contintue....

---

### Post by Elfy on 2009-03-13
> rootnoverify (hd1.0)

should be

> rootnoverify (hd1,0)

same for the other possibles

---

### Post by meierfra. on 2009-03-13
Thanks, forestpixie.

---

### Post by elliotn on 2009-03-13
K thanks guys the first option worked. 

 
Problem Solved.

---

### Post by Elfy on 2009-03-13
> **meierfra. said:**
> Thanks, forestpixie.

No idea why the original menu had that either though?

---

### Post by meierfra. on 2009-03-13
> No idea why the original menu had that either though?
Now I understand. To save typing, I had copied the entry from the original menu  and then edited it.  But I hadn't  noticed that typo in the original menu until you told me.


> Problem Solved. 
Great. Have fun with XP and Ubuntu.

---

