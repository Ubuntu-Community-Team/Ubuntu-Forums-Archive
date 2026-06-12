---
title: "Can GRUB boot a frugal Ubuntu Installation?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by kac0802 on 2009-05-05
I have just installed Ubuntu to my flash drive and I am putting grub on it as well so that I can choose between a couple of different OS's to boot off my flash drive. I can not figure out how to refer to the frugal, or usb, installation of Ubuntu in grub. Does anyone know how to do this?

PS: I am sorry if this is posted somewhere else on these forums, but I looked for a long time here, and all over the internet for a solution and could not find one.

Thanks, 
Kaleb

---

### Post by caljohnsmith on 2009-05-05
So what method did you use to install Ubuntu to your flash drive? Also, when it comes to booting issues, a good place to start is to download the **Boot Info Script** to your Ubuntu desktop (can be a Live CD desktop):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it might take to boot your OSes on your flash drive.

John

---

### Post by kac0802 on 2009-05-06
I used the usb installer (System > Administration > USB Startup Disk Creator). 
I haven't finished setting up the grub *menu.lst* file yet. So far, I just copied it from my hard drive install and changed the first entry in attempt to make it bootable.

Here are the results of the Boot Info Script:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 63. According to the info in the 
                       boot sector, sdb2 has 0 sectors.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2107a38

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,595,200   162,595,199   150,000,000   7 HPFS/NTFS
/dev/sda3         162,609,930   312,576,704   149,966,775   5 Extended
/dev/sda5         164,939,355   312,576,704   147,637,350  83 Linux
/dev/sda6         162,610,056   164,923,289     2,313,234  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000710b4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         48,195    15,679,439    15,631,245   c W95 FAT32 (LBA)
/dev/sdb2                  63        48,194        48,132   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="468C4F3A8C4F2431" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="7E5811A858115FE7" TYPE="ntfs" 
/dev/sda5: UUID="9a9cc024-2520-4183-a7bf-52c7fd0a91fb" TYPE="ext4" 
/dev/sda6: UUID="c2077751-5128-4562-8040-bf2e3f08422a" TYPE="swap" 
/dev/sdb1: UUID="E9CE-284B" TYPE="vfat" 
/dev/sdb2: SEC_TYPE="msdos" UUID="039B-6C6C" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/kaleb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kaleb)
/dev/sdb2 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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

#A splash image for the menu
#splashimage=/boot/grub/splashimages/gunhole.xpm.gz

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
# kopt=root=UUID=9a9cc024-2520-4183-a7bf-52c7fd0a91fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a9cc024-2520-4183-a7bf-52c7fd0a91fb

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
uuid        9a9cc024-2520-4183-a7bf-52c7fd0a91fb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a9cc024-2520-4183-a7bf-52c7fd0a91fb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9a9cc024-2520-4183-a7bf-52c7fd0a91fb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a9cc024-2520-4183-a7bf-52c7fd0a91fb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9a9cc024-2520-4183-a7bf-52c7fd0a91fb
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
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9a9cc024-2520-4183-a7bf-52c7fd0a91fb /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c2077751-5128-4562-8040-bf2e3f08422a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  88.7GB: boot/grub/menu.lst
  86.2GB: boot/grub/stage2
  89.0GB: boot/initrd.img-2.6.28-11-generic
  86.3GB: boot/vmlinuz-2.6.28-11-generic
  89.0GB: initrd.img
  86.3GB: vmlinuz

============================= sdb2/grub/menu.lst: =============================

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
default        saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/gentleblue.xpm.gz

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
# kopt=root=UUID=9a9cc024-2520-4183-a7bf-52c7fd0a91fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a9cc024-2520-4183-a7bf-52c7fd0a91fb

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

title        Ubuntu 9.04
root        (hd0,1)
kernel        /casper/vmlinuz
initrd        /casper/initrd.gz
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9a9cc024-2520-4183-a7bf-52c7fd0a91fb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a9cc024-2520-4183-a7bf-52c7fd0a91fb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86 
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
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=================== sdb2: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
```

---

### Post by floborg on 2009-05-06
> **kac0802 said:**
> I have just installed Ubuntu to my flash drive and I am putting grub on it as well so that I can choose between a couple of different OS's to boot off my flash drive. I can not figure out how to refer to the frugal, or usb, installation of Ubuntu in grub. Does anyone know how to do this?

PS: I am sorry if this is posted somewhere else on these forums, but I looked for a long time here, and all over the internet for a solution and could not find one.

Thanks, 
Kaleb

I know.  You need to use the majic "iso-scan" boot parameter.  First, extract the kernel and initrd from the ISO.  Then, put all three files in some directory.  Finally, add something like this to menu.lst:

```
title     Ubuntu 9.04 i386 (from ISO)
kernel    (hd0,2)/fromiso/vmlinuz iso-scan/filename=/fromiso/ubuntu-9.04-desktop-i386.iso boot=casper quiet splash
initrd    (hd0,2)/fromiso/initrd.gz
```

---

