---
title: "GRUB error 17..."
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by blah... on 2009-10-25
Hi guys, so yesterday I decided to transfer my Wubi install into a dedicated partiton using LVPM. But when I rebooted, error 17 comes out and I have no idea what to do... Help would be appreciated. Also, I'm on the live CD just in case I need to do something with it.

---

### Post by blah... on 2009-10-25
Anyone?

---

### Post by hal10000 on 2009-10-25
This is from the grub documentation:

> 17 : Cannot mount selected partition

    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.


It seems as if grub does'nt recognize the filesystem of your boot partition.

Please post the output of 
```
 sudo fdisk -l
```

and 
```
 cat /boot/grub/menu.lst
```

---

### Post by blah... on 2009-10-25
> **hal10000 said:**
> This is from the grub documentation:



It seems as if grub does'nt recognize the filesystem of your boot partition.

Please post the output of 
```
 sudo fdisk -l
```and 
```
 cat /boot/grub/menu.lst
```ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d1df933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  12  Compaq diagnostics
/dev/sda2   *         893        5333    35672332+   6  FAT16
/dev/sda3            5334        7870    20374804    7  HPFS/NTFS
/dev/sda4            7870        9730    14937088    f  W95 Ext'd (LBA)
/dev/sda5            7870        9730    14936064   83  Linux
ubuntu@ubuntu:~$ 

as for the next one I can't seem to use it...

---

### Post by oldfred on 2009-10-25
I do not know how the LMPM works in coping wubi to a real partition. It seems like something may be missing. Try downloading and running this script to document your entire booting process:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by blah... on 2009-10-25
> **oldfred said:**
> I do not know how the LMPM works in coping wubi to a real partition. It seems like something may be missing. Try downloading and running this script to document your entire booting process:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d1df933

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    14,329,979    14,329,917  12 Compaq diagnostics
/dev/sda2    *     14,329,980    85,674,644    71,344,665   6 FAT16
/dev/sda3          85,674,645   126,424,252    40,749,608   7 HPFS/NTFS
/dev/sda4         126,425,088   156,299,263    29,874,176   f W95 Ext d (LBA)
/dev/sda5         126,427,136   156,299,263    29,872,128  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="28D8C1A516D9B5D2" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="76C02BD5C02B9A7F" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="A6DC0EFADC0EC511" LABEL="DATA (D:) " TYPE="ntfs" 
/dev/sda5: UUID="c37ba8ce-8911-4149-83d9-cafd6f7896ce" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


==================== sda3/ubuntu/disks/boot/grub/menu.lst: ====================

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
timeout        3

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
# kopt=root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=A6DC0EFADC0EC511 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1



title Ubuntu-on-/dev/sda5
root (hd0,4)
configfile /boot/grub/menu.lst



======================== sda3/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================== sda3Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda3: Location of files loaded by Grub: ===================


  62.4GB: ubuntu/disks/boot/grub/menu.lst
  51.8GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  51.7GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
  51.7GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
  51.7GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
  51.6GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic
  51.6GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic

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
timeout        3

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
# kopt=root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


title Windows
root (hd0,2)
makeactive
chainloader +1
boot


title Windows NT/2000/XP
root (hd0,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd0,1)
makeactive
chainloader +1
boot


=============================== sda5/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda5
UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=A6DC0EFADC0EC511       /media/drv0       ntfs-3g         defaults      0   0


=================== sda5: Location of files loaded by Grub: ===================


  66.5GB: boot/grub/menu.lst
  66.6GB: boot/grub/stage2
  66.6GB: boot/initrd.img-2.6.28-11-generic
  66.6GB: boot/initrd.img-2.6.28-15-generic
  66.5GB: boot/initrd.img-2.6.28-16-generic
  66.5GB: boot/vmlinuz-2.6.28-11-generic
  66.5GB: boot/vmlinuz-2.6.28-15-generic
  66.5GB: boot/vmlinuz-2.6.28-16-generic
  66.5GB: initrd.img
  66.6GB: initrd.img.old
  66.5GB: vmlinuz
  66.5GB: vmlinuz.old
``` There you go. And thanks for showing me how to do that, I've seen other posts here with the code font but I wasn't aware how to do that.

---

### Post by oldfred on 2009-10-25
The first thing I see is that the menu.lst in sda5 does not have a normal root command, it looks like it just copies the sda3 wubi entry:

root        ()/ubuntu/disks

should be for sda5:
root        (hd0,4)

The newer alternative is using sda5's uuid
uuid        c37ba8ce-8911-4149-83d9-cafd6f7896ce

Try these changes and if not I will see if I missing something else.

---

### Post by oldfred on 2009-10-25
Does it install Grub in the MBR?

You have a chainboot entry in your wubi menu.lst but for the chainboot to work grub has to be installed in the partition.

Do you want to use grub to boot from the MBR and choose windows or ubuntu which is the standard way? Or use the wubi style where you still boot windows and choose windows, wubi or the partition install? It will make a difference on whether you need to install grub to the MBR or to the partition PBR or VBR in some nomenclatures.

---

### Post by blah... on 2009-10-25
> **oldfred said:**
> Does it install Grub in the MBR?

You have a chainboot entry in your wubi menu.lst but for the chainboot to work grub has to be installed in the partition.

Do you want to use grub to boot from the MBR and choose windows or ubuntu which is the standard way? Or use the wubi style where you still boot windows and choose windows, wubi or the partition install? It will make a difference on whether you need to install grub to the MBR or to the partition PBR or VBR in some nomenclatures.Yes it installs grub, which is were I got the error. It shows all the OS's but when I choose Ubuntu the error comes out. If I boot Windows the wubi boot screen comes up as usual.

---

### Post by blah... on 2009-10-25
> **oldfred said:**
> The first thing I see is that the menu.lst in sda5 does not have a normal root command, it looks like it just copies the sda3 wubi entry:

root        ()/ubuntu/disks

should be for sda5:
root        (hd0,4)

The newer alternative is using sda5's uuid
uuid        c37ba8ce-8911-4149-83d9-cafd6f7896ce

Try these changes and if not I will see if I missing something else.I've also tried that but what happens is that instead of booting into the partiton, it boots into the data section of Vista, which is were Wubi is, so its like booting into Wubi.

---

### Post by louieb on 2009-10-25
> **blah... said:**
>  But when I rebooted, error 17 comes out and I have no idea what to do...

Exctly where do you get the grub error 17. Do you see the Gurb menu? If so what entries are giving you the error?

Never mind just saw this.

> Yes it installs grub, which is were I got the error. It shows all the OS's but when I choose Ubuntu the error comes out. If I boot Windows the wubi boot screen comes up as usual.

anyway you need to change   /boot/grub/menu.lst .( [COLOR=Purple]the menu.lst in sda5[/COLOR]) replace the [COLOR=Red]root[/COLOR] line with a uuid line. You will find several root lines - change all - should look like this. 
```

title        Ubuntu 9.04, kernel 2.6.28-16-generic
[COLOR=Red]uuid       c37ba8ce-8911-4149-83d9-cafd6f7896ce[/COLOR]
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic


```also 
change the groot line from
```
# groot=()/ubuntu/disks
```to

```
# groot=c37ba8ce-8911-4149-83d9-cafd6f7896ce
```

---

### Post by blah... on 2009-10-25
> **louieb said:**
> Exctly where do you get the grub error 17. Do you see the Gurb menu? If so what entries are giving you the error?

Never mind just saw this.



anyway you need to change   /boot/grub/menu.lst .( [COLOR=Purple]the menu.lst in sda5[/COLOR]) replace the [COLOR=Red]root[/COLOR] line with a uuid line. You will find several root lines - change all - should look like this. 
```

title        Ubuntu 9.04, kernel 2.6.28-16-generic
[COLOR=Red]uuid       c37ba8ce-8911-4149-83d9-cafd6f7896ce[/COLOR]
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic


```also 
change the groot line from
```
# groot=()/ubuntu/disks
```to

```
# groot=c37ba8ce-8911-4149-83d9-cafd6f7896ce
```Great! Now were can I make the changes lol...

---

### Post by oldfred on 2009-10-25
I always like to backup just incase the changes are not quite right.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then to edit menu.lst scroll down to all the ubuntu lines and update the root command to uuid command as posted above.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by blah... on 2009-10-25
> **louieb said:**
> Exctly where do you get the grub error 17. Do you see the Gurb menu? If so what entries are giving you the error?

Never mind just saw this.



anyway you need to change   /boot/grub/menu.lst .( [COLOR=Purple]the menu.lst in sda5[/COLOR]) replace the [COLOR=Red]root[/COLOR] line with a uuid line. You will find several root lines - change all - should look like this. 
```

title        Ubuntu 9.04, kernel 2.6.28-16-generic
[COLOR=Red]uuid       c37ba8ce-8911-4149-83d9-cafd6f7896ce[/COLOR]
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic


```also 
change the groot line from
```
# groot=()/ubuntu/disks
```to

```
# groot=c37ba8ce-8911-4149-83d9-cafd6f7896ce
```Including these:
```
title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic[COLOR=Red] root=UUID=c37ba8ce-8911-4149-83d9-cafd6f7896ce  ro quiet splash[/COLOR] 
initrd        /boot/initrd.img-2.6.28-16-generic
```Sorry bout all the questions guys, I'm a complete noob at this and I don't want to screw up my system...

---

### Post by louieb on 2009-10-25
Replace just the lines that start with root . The root parameter on the kernel line is fine the way it is.

---

### Post by blah... on 2009-10-25
> **louieb said:**
> Replace just the lines that start with root . The root parameter on the kernel line is fine the way it is.Ha, ha, it worked! Thanks to all that helped :D

---

