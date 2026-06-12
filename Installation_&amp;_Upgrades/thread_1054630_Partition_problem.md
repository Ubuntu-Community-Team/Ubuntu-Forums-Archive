---
title: "Partition problem"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by seattle vic on 2009-01-29
I guess it's time I learned more about partitions.  I have a laptop with 2 HD's.  When it came new, I left sda alone, and installed Ubuntu on sdb.  No problems, and I was able to dual boot to vista when needed, which was only for the occasional game distraction.

Soooo, the other day I decided to try and install 64 bit Ubuntu.  Since I'd set up the Ubuntu installer for 1 partition on sdb, I decided to use the extended partion in sda.  It installed OK, and is usable, as is vista, but something happened, because now when I try and boot either Ubuntu, it bogs down with errors - mostly that seem to relate to sda, etc.  It slogs through these after about 5 minutes, then boots and works OK.

The layout in sda that came with the machine was:

/dev/sda1      fat32       9.77G (labeled RECOVERY)
/dev/sda2      ntfs        116.4
/dev/sda3      extended    106.68
   /dev/sda5   ext3        106.68

I believe that when I wrote the 64 bit sys from the live disk to the hard drive, it showed sda5 and that's what I chose.

The other interesting thing is that I can no longer view the contents of sda2 as I used to from nautilus, although vista does boot fine (and without the delay).

I'm tempted to re-install 64 bit using the entire disk, and blow vista away, though I'd still like to have it handy (even though it is a pos).

Is there a simple way to fix/correct this?  I don't even know what I did wrong.  If I was to re-partition sda and re-install vista, with a 2nd partition for 64 ubuntu, how would I go about it with a cleaner result?

Thanks in advance

---

### Post by caljohnsmith on 2009-01-29
How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d

```

---

### Post by seattle vic on 2009-01-29
> **caljohnsmith said:**
> How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d

```

You bet:

vic@vic-laptop:~$ sudo fdisk -lu
[sudo] password for vic: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20482874    10241406   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    20482875   264670874   122094000   17  Hidden HPFS/NTFS
/dev/sda3       264670875   488392064   111860595    f  W95 Ext'd (LBA)
/dev/sda5       264670938   488392064   111860563+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84f5997e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   470174354   235087146   83  Linux
/dev/sdb2       470174355   488392064     9108855    5  Extended
/dev/sdb5       470174418   488392064     9108823+  82  Linux swap / Solaris

vic@vic-laptop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20482812, Id=1c
/dev/sda2 : start= 20482875, size=244188000, Id=17, bootable
/dev/sda3 : start=264670875, size=223721190, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=264670938, size=223721127, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=470174292, Id=83
/dev/sdb2 : start=470174355, size= 18217710, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=470174418, size= 18217647, Id=82
vic@vic-laptop:~$

---

### Post by caljohnsmith on 2009-01-29
> **seattle vic said:**
> 
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20482874    10241406   1c  [COLOR="Blue"]Hidden W95 FAT32[/COLOR] (LBA)
/dev/sda2   *    20482875   264670874   122094000   17  [COLOR="Blue"]Hidden HPFS/NTFS[/COLOR]
/dev/sda3       264670875   488392064   111860595    f  W95 Ext'd (LBA)
/dev/sda5       264670938   488392064   111860563+  83  Linux

```

I looked it over carefully, and your partition table table looks just fine to me. But as I have highlighted above, for some reason your sda1 and sda2 partitions were "hidden" at some point, so it would be good to unhide them. How about doing:
```
sudo grub
grub> unhide (hd0,0)
grub> unhide (hd0,1)
grub> quit
```
And that should hopefully fix that problem. But I'm not sure why you would be having problems with the Ubuntu install, because like I said, at least your partition table looks good. I think it might help if you installed with a swap partition--is there some reason why you chose not to do that? Just curious.

---

### Post by seattle vic on 2009-01-29
> **caljohnsmith said:**
> I looked it over carefully, and your partition table table looks just fine to me. But as I have highlighted above, for some reason your sda1 and sda2 partitions were "hidden" at some point, so it would be good to unhide them. How about doing:
```
sudo grub
grub> unhide (hd0,0)
grub> unhide (hd0,1)
grub> quit
```
And that should hopefully fix that problem. But I'm not sure why you would be having problems with the Ubuntu install, because like I said, at least your partition table looks good. I think it might help if you installed with a swap partition--is there some reason why you chose not to do that? Just curious.

I did the unhide thing and it did unhide the two partitions, but ubuntu is still choking on boot-up.  It does seem odd that booting up on sdb creates errors re: sda though.

On the swap partition, my mistake.  I was in a hurry and forgot.

---

### Post by caljohnsmith on 2009-01-30
I think it would help to get more info about your system, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully give some clues what your booting problem might be.

---

### Post by seattle vic on 2009-01-31
> **caljohnsmith said:**
> I think it would help to get more info about your system, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully give some clues what your booting problem might be.

OK, here it is:
===============================================================

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812   c W95 FAT32 (LBA)
/dev/sda2    *     20,482,875   264,670,874   244,188,000   7 HPFS/NTFS
/dev/sda3         264,670,875   488,392,064   223,721,190   f W95 Ext'd (LBA)
/dev/sda5         264,670,938   488,392,064   223,721,127  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84f5997e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   470,174,354   470,174,292  83 Linux
/dev/sdb2         470,174,355   488,392,064    18,217,710   5 Extended
/dev/sdb5         470,174,418   488,392,064    18,217,647  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: UUID="88B4C2D3B4C2C344" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="5f0ed58e-9e16-4515-89c9-24c30d22a0d5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="e0501242-0e12-4c39-8a54-1be6acd3444a" TYPE="ext3" 
/dev/sdb5: UUID="db011b17-d833-47a2-81dd-b0140206cfc7" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/vic/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vic)

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
# kopt=root=UUID=5f0ed58e-9e16-4515-89c9-24c30d22a0d5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f0ed58e-9e16-4515-89c9-24c30d22a0d5

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

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-10-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro single 
initrd		/boot/initrd.img-2.6.27-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-8-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro single 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot



title		Ubuntu 8.10, kernel 2.6.27-9-generic (64 bit)
uuid		5f0ed58e-9e16-4515-89c9-24c30d22a0d5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5f0ed58e-9e16-4515-89c9-24c30d22a0d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (64 bit, recovery mode)
uuid		5f0ed58e-9e16-4515-89c9-24c30d22a0d5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5f0ed58e-9e16-4515-89c9-24c30d22a0d5 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (64 bit)
uuid		5f0ed58e-9e16-4515-89c9-24c30d22a0d5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5f0ed58e-9e16-4515-89c9-24c30d22a0d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (64 bit, recovery mode)
uuid		5f0ed58e-9e16-4515-89c9-24c30d22a0d5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5f0ed58e-9e16-4515-89c9-24c30d22a0d5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5f0ed58e-9e16-4515-89c9-24c30d22a0d5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader, recovery mode)
root		(hd0,0)
savedefault
makeactive
chainloader	+1






=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5f0ed58e-9e16-4515-89c9-24c30d22a0d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=db011b17-d833-47a2-81dd-b0140206cfc7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


 177.8GB: boot/grub/menu.lst
 177.8GB: boot/grub/stage2
 177.8GB: boot/initrd.img-2.6.27-7-generic
 177.8GB: boot/initrd.img-2.6.27-9-generic
 177.7GB: boot/vmlinuz-2.6.27-7-generic
 177.7GB: boot/vmlinuz-2.6.27-9-generic
 177.8GB: initrd.img
 177.8GB: initrd.img.old
 177.7GB: vmlinuz
 177.7GB: vmlinuz.old

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
# kopt=root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0501242-0e12-4c39-8a54-1be6acd3444a

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
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0501242-0e12-4c39-8a54-1be6acd3444a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e0501242-0e12-4c39-8a54-1be6acd3444a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn - loader (recovery mode)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e0501242-0e12-4c39-8a54-1be6acd3444a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=db011b17-d833-47a2-81dd-b0140206cfc7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location  of files loaded by Grub: ===================


  82.6GB: boot/grub/menu.lst
  82.6GB: boot/grub/stage2
  82.6GB: boot/initrd.img-2.6.27-10-generic
  82.6GB: boot/initrd.img-2.6.27-11-generic
  82.5GB: boot/initrd.img-2.6.27-7-generic
  82.6GB: boot/initrd.img-2.6.27-8-generic
  82.6GB: boot/vmlinuz-2.6.27-10-generic
  82.5GB: boot/vmlinuz-2.6.27-11-generic
  82.6GB: boot/vmlinuz-2.6.27-7-generic
  82.6GB: boot/vmlinuz-2.6.27-8-generic
  82.6GB: initrd.img
  82.6GB: initrd.img.old
  82.5GB: vmlinuz
  82.6GB: vmlinuz.old

---

### Post by caljohnsmith on 2009-01-31
As far as I can tell based on the info the script provided, everything about your setup looks to be in order. What exactly are the errors you get on start up? That might give some better clues what the problem is.

---

