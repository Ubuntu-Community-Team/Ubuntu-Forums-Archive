---
title: "Sil3114 RAID 5 array problems"
date: 2009-07-16
forum: Hardware
---

### Post by Platypus123 on 2009-07-16
I'm having a bit of an issue with Ubuntu 9.04 reading my PCI Sil3114 RAID 5 NTFS array.  

I've got a pair of mirrored WD Raptors (Not on the RAID 5 card) running Vista, and I have Ubuntu installed on a separate hard drive (also not on the array).  I didn't like the dual-boot option and decided to go separate hard drives for my Linux/Windows setup instead.  (To summarize: 3 drives in a PCI RAID 5 array, two drives in motherboard RAID 0 running Vista, and a single drive running Ubuntu)

Ubuntu will recognize the Vista drives (by mounting with the NTFS application, although not as an array but as two separate drives, and it won't see my RAID 5 drives at all.  When DMraid is installed, nothing changes in regards to the Vista drives, but I can see the 3 RAID 5 drives, although again, not as an array but as 3 separate drives.

When I reboot my computer with DMRaid installed, Ubuntu won't boot at all.  When I disconnect the RAID 5 drives it loads fine again and I have to uninstall DMraid if I want the drives connected again on boot.  

Ideally, I'd like to be able to have my Vista drives recognized as a mirrored array (as one drive, not two), as well as be able to read my RAID 5 array.  

When I ran Ubuntu in the past, I had used the dual boot option (Had Vista and Ubuntu both running off of the RAID 5 array (Before I owned the Raptors) and it worked fine.  I believe I had to load the sil3114 driver during installation for it to read the array in order to install.  I believe I've downloaded the correct sil3114 drivers, but as it's been a while since I've used Linux, I can't remember how to install anything that isn't in the Synaptics Package Manager.

Any help in this regard would be greatly appreciated.

---

### Post by Platypus123 on 2009-07-18
Here's some new information that might shed light on a solution:  

When I installed Ubuntu on the separate hard drive, I had disconnected all other drives as to not ruin anything on the RAID 5 array or on my Windows array.  After installation, I reconnected the drives and it booted just fine.  After installing dmraid to manage the arrays, Ubuntu would not boot (unless the array drives are disconnected, or until dmraid was uninstalled) and would just hang at the grub-loading bootup page.  My understanding is that the array drives reclassified the hard disk name of my Ubuntu drive from (hd0,1) to (hd3,1) as per grub because it says it's still trying to load from (hd0,1)

I've been tinkering with menu.lst, and with the grub prompt, but have not been able to figure it out.  

Grub prompt:
> grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd3,1)

Here is a description of 'fdisk -l' that shows my Ubuntu installation at sdd2: 
> 
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ee08d83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9791    78643200    7  HPFS/NTFS
/dev/sda2            9791       13055    26214400    7  HPFS/NTFS
/dev/sda3           13055       61031   385372160    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ee08d83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9791    78643200    7  HPFS/NTFS
/dev/sdb2            9791       13055    26214400    7  HPFS/NTFS
/dev/sdb3           13055       61031   385372160    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         249     2000061   82  Linux swap / Solaris
/dev/sdd2   *         250        3984    30001387+  83  Linux
/dev/sdd3            3985        9730    46146560    7  HPFS/NTFS

Disk /dev/sde: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8578505

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdf: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8578505

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        9040    72610816    7  HPFS/NTFS

And now here is a description of menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default saved

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
# kopt=root=/dev/sdd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,1)

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro quiet splash acpi=off 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro quiet splash acpi=off 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Hopefully the solutions presents itself to someone out there.  Please note that because of my 'noob' status, I'll need step-by-step directions.  Thanks.

---

### Post by Platypus123 on 2009-07-25
Alright.  It's been an interesting week learning Linux! I'm making a bit of headway on my own, but am surprised that no one has said anything yet.

I managed to get around the dmraid issue by installing RC14 instead of the newer RC15.  No problems on boot with RC14, but my RAID 5 NTFS drives are no longer self mounting (i.e. I can't "see" them in Nautilus).  

To give further details which may prompt a few suggestions, I have 3 partitions on 3 250GB drives in a NTFS RAID 5 array. Here is what dmraid shows:

> root@daniel-desktop:~# dmraid -ay
/dev/sde: "sil" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_bafbhfhh" already active
RAID set "nvidia_eabcedeg" already active
RAID set "sil_aiaecbceccag" already active
RAID set "nvidia_bafbhfhh1" already active
RAID set "nvidia_eabcedeg1" already active
RAID set "nvidia_eabcedeg5" already active
RAID set "sil_aiaecbceccag1" already active
RAID set "sil_aiaecbceccag2" already active
RAID set "sil_aiaecbceccag3" already active
root@daniel-desktop:~# 


> root@daniel-desktop:~# dmraid -tay
/dev/sde: "sil" and "nvidia" formats discovered (using nvidia)!
nvidia_bafbhfhh: 0 145226110 mirror core 2 131072 nosync 2 /dev/sdf 0 /dev/sdg 0 1 handle_errors
nvidia_eabcedeg: 0 156301486 linear /dev/sde 0
sil_aiaecbceccag: 0 980466176 raid45 core 2 131072 nosync raid5_ls 1 128 3 -1 /dev/sda 0 /dev/sdb 0 /dev/sdc 0
nvidia_bafbhfhh1: 0 145221632 linear /dev/mapper/nvidia_bafbhfhh 2048
nvidia_eabcedeg1: 0 150368337 linear /dev/mapper/nvidia_eabcedeg 63
nvidia_eabcedeg5: 0 5927922 linear /dev/mapper/nvidia_eabcedeg 150368463
sil_aiaecbceccag1: 0 157286400 linear /dev/mapper/sil_aiaecbceccag 2048
sil_aiaecbceccag2: 0 52428800 linear /dev/mapper/sil_aiaecbceccag 157288448
sil_aiaecbceccag3: 0 770744320 linear /dev/mapper/sil_aiaecbceccag 209717248
root@daniel-desktop:~#

> root@daniel-desktop:~# dmraid -r
/dev/sde: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdg: nvidia, "nvidia_bafbhfhh", mirror, ok, 145226110 sectors, data@ 0
/dev/sdf: nvidia, "nvidia_bafbhfhh", mirror, ok, 145226110 sectors, data@ 0
/dev/sde: nvidia, "nvidia_eabcedeg", linear, ok, 156301486 sectors, data@ 0
/dev/sdc: sil, "sil_aiaecbceccag", raid5_ls, ok, 490233214 sectors, data@ 0
/dev/sdb: sil, "sil_aiaecbceccag", raid5_ls, ok, 490233214 sectors, data@ 0
/dev/sda: sil, "sil_aiaecbceccag", raid5_ls, ok, 490233214 sectors, data@ 0
root@daniel-desktop:~# 


'nvidia' is my Raptors in a NTFS Raid 1 array and 'sil' are my 3x250GB drives in a NTFS Raid 5 array.  

My question is, how do I go about mounting the partitions in Ubuntu?  I'm aware of the 'mount -t ntfs' command, but I can't figure out how it pertains to my setup (3 partitions on 3 drives for the RAID 5 array).  Help!

---

### Post by Platypus123 on 2009-08-14
I obliterated Vista and reformatted all NTFS drives to EXT4.  I've had enough of Windows anyway. EXT4 is much faster! It's like SSD speeds!  I moved the date off of my array first and implemented a software RAID with MDADM.  

Thanks!

---

