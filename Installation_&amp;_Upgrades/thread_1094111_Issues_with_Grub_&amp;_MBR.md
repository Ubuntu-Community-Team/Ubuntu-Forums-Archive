---
title: "Issues with Grub &amp; MBR"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by gogobambi on 2009-03-12
I'm having serious issues with Grub and the MBR.

HDD1 - 250GB
HDD2 - 500GB
HDD3 (new) - 1TB

Originally I had Ubuntu 8.10 server installed on HDD1, with data on HDD2. I used Gparted from an Ubuntu Live USB to move the system partitions from HDD1 to HDD2 and moved my data from HDD2 to HDD3. I installed Grub on HDD2's MBR using:

sudo grub
find /grub/stage1 [boot was on a separate partition]
(hd0,1)
root (hd0,1)
setup (hd0)

Everything checked out fine, but when I restart, minus the Live USB, the BIOS can't find a bootable device. BIOS and boot settings are all fine and all the HDDs are SATA, running on an Intel Dual-core Atom (D945GCLF2). Anyone have any ideas?

---

### Post by TrickerZ on 2009-03-12
Is the BIOS set to boot off that drive?

---

### Post by Neo_The_User on 2009-03-12
Terminal:

```

sudo update-grub

```

or edit menu.lst by hand however update-grub will probe everything.

---

### Post by gogobambi on 2009-03-12
The BIOS is correctly configured and I've tried just about every configuration on there, which is silly given it was booting fine before from the 250GB.

Ran update-grub, but it hasn't changed anything. To get it to update the right grub I had to mount the partitions and chroot into /mnt/root, following [this post]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1").

If it was getting past the MBR and booting into grub and then getting an error, the message would be different from the BIOS message of "No bootable devices -- insert boot disk and press any key", right? Could there be something wrong with the MBR?

---

### Post by gogobambi on 2009-03-12
Here are the results from the Boot Info Script and a list of the partitions:

sda (500GB) = Ubuntu Server 8.10
*sda1 = swap
*sda2 = /boot
*sda3 = /root
*sda4 = extended partition
**sda5 = /tmp
**sda6 = /var
**sda7 = /home
**sda8 = /torrentflux (user directory)

sdb (1TB) = data
*sdb1 = /serv (user directory)

sdc (1GB) = Ubuntu Desktop Live 8.10 USB drive

EDIT: edited the fstab, changing sdb to sda and vice versa and correcting the UUIDs, still get the same boot error.
 
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000870b8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     5,863,724     5,863,662  82 Linux swap / Solaris
/dev/sda2           5,863,725     6,361,739       498,015  83 Linux
/dev/sda3           6,361,740    16,129,259     9,767,520  83 Linux
/dev/sda4          16,129,260   976,768,064   960,638,805   5 Extended
/dev/sda5          16,129,323    20,033,054     3,903,732  83 Linux
/dev/sda6          20,033,118    27,840,644     7,807,527  83 Linux
/dev/sda7          27,840,708    37,608,164     9,767,457  83 Linux
/dev/sda8          37,608,228   976,768,064   939,159,837  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4ec2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,966,079     1,966,048   b W95 FAT32

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="73dda411-69df-4244-8b56-0ec9de5b224e" TYPE="swap" 
/dev/sda2: UUID="3ba9f3f6-6602-43da-a1ef-b91236e0dd54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="f3e0fc03-0227-411c-bb3c-a82174088e2e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="95de292c-ab20-4479-afa4-7090a8ea9710" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="2fa40d6d-e2ef-486b-80f1-3a50bc3b0b1c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="5685e9b8-56c5-4945-b2de-1b75a8777d43" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="b783386a-c0b5-47d6-87ec-7667a8cf727c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="207ffc43-421d-4750-8913-df4037b84ad7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="UBUNTU" UUID="806A-8F8F" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="dbab47ea-fade-49cd-8c50-d18d8f673dee" TYPE="ext3" 

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
/dev/sdd1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev on /mnt/root/dev type none (rw,bind)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================= sda2/grub/menu.lst: =============================

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
# kopt=root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3ba9f3f6-6602-43da-a1ef-b91236e0dd54

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

title		Ubuntu 8.10, kernel 2.6.27-11-server
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/vmlinuz-2.6.27-11-server root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro quiet splash 
initrd		/initrd.img-2.6.27-11-server
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-server (recovery mode)
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/vmlinuz-2.6.27-11-server root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro  single
initrd		/initrd.img-2.6.27-11-server

title		Ubuntu 8.10, kernel 2.6.27-9-server
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/vmlinuz-2.6.27-9-server root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro quiet splash 
initrd		/initrd.img-2.6.27-9-server
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-server (recovery mode)
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/vmlinuz-2.6.27-9-server root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro  single
initrd		/initrd.img-2.6.27-9-server

title		Ubuntu 8.10, kernel 2.6.27-7-server
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/vmlinuz-2.6.27-7-server root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro quiet splash 
initrd		/initrd.img-2.6.27-7-server
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode)
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/vmlinuz-2.6.27-7-server root=UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e ro  single
initrd		/initrd.img-2.6.27-7-server

title		Ubuntu 8.10, memtest86+
uuid		3ba9f3f6-6602-43da-a1ef-b91236e0dd54
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda2: Location of files loaded by Grub: ===================


   3.1GB: grub/menu.lst
   3.1GB: grub/stage2
   3.0GB: initrd.img-2.6.27-11-server
   3.0GB: initrd.img-2.6.27-7-server
   3.0GB: initrd.img-2.6.27-9-server
   3.0GB: vmlinuz-2.6.27-11-server
   3.0GB: vmlinuz-2.6.27-7-server
   3.0GB: vmlinuz-2.6.27-9-server

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=f3e0fc03-0227-411c-bb3c-a82174088e2e /               ext3    relatime,errors=remount-ro,noatime,nodiratime 0       1
# /dev/sdb2
UUID=3ba9f3f6-6602-43da-a1ef-b91236e0dd54 /boot           ext3    relatime,noatime,nodiratime        0       2
# /dev/sdb7
UUID=5685e9b8-56c5-4945-b2de-1b75a8777d43 /home           ext3    relatime,noatime,nodiratime        0       2
# /dev/sda1
UUID=a2f78597-f7d7-455c-9332-0a9ede34663a /serv           ext3    relatime,noatime,nodiratime        0       2
# /dev/sdb8
UUID=4e47be90-8bbd-4816-9f62-75d56e089137 /torrentflux    ext3    relatime,noatime,nodiratime        0       2
# /dev/sdb5
UUID=95de292c-ab20-4479-afa4-7090a8ea9710 /tmp            ext3    relatime,noatime,nodiratime        0       2
# /dev/sdb6
UUID=2fa40d6d-e2ef-486b-80f1-3a50bc3b0b1c /var            ext3    relatime,noatime,nodiratime        0       2
# /dev/sdb1
UUID=fa31582d-845e-4282-a5dc-013f244f8e47 none            swap    sw              0       0

```

---

### Post by meierfra. on 2009-03-12
Some bios refuse to boot a hard drive which does not have an active primary partition. So I suggest to set a boot flag to your boot partition:
Boot from the LiveCD, open a terminal and type

```
sudo sfdisk -A2 /dev/sda
```

Maybe that's enough to solve your problem.

---

### Post by gogobambi on 2009-03-12
Yes, that fixes it. Thanks meierfra!

---

### Post by meierfra. on 2009-03-15
> Yes, that fixes it. 

Great. Have fun with Ubuntu.

---

