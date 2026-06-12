---
title: "Impossible to access partition of a Hard-Drive"
date: 2011-03-12
forum: Hardware
---

### Post by fluo75 on 2011-03-12
Hi,

I have a problem under KUbuntu.
Ubuntu can access the partitions of my second Hard-Drive but not of my first Hard Drive.

Here are some information about this Hard-Drive:


```
**sudo df -kTh /dev/sda**
Sys. de fich. Type    Taille  Uti. Disp. Uti% Monté sur
none      devtmpfs    2,0G  320K  2,0G   1% /dev

```

```
**sudo parted -l /dev/sda**
Erreur: On ne peut avoir de partitions qui se chevauchent.   *(meaning You can not have overlapping partitions.)           * 

Modèle: ATA WDC WD2500BEVS-6 (scsi)
Disque /dev/sdb : 250GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      32,3kB  242GB  242GB   primary   ntfs
 2      242GB   250GB  8455MB  extended
 5      242GB   250GB  8040MB  logical   ext4

```


```
**sudo fdisk -l /dev/sda**

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x80b583ca

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1          13      101376    7  HPFS/NTFS
La partition 1 ne se termine pas sur une frontière de cylindre.
*(meaning Partition 1 does not end on cylinder boundary)*
/dev/sda2        ave       14       37676   302528047+   f  W95 Etendue (LBA)
/dev/sda3           19123       37511   147704832    7  HPFS/NTFS
/dev/sda5              14        1580    12585903+  83  Linux
/dev/sda6            1581        2039     3686886   83  Linux
/dev/sda7            2040       19123   137214976    7  HPFS/NTFS
/dev/sda8           37512       37676     1325331   82  Linux swap / Solaris

```

Do you have any ideas how I could solve this problem?

Thanks in advance,

David

---

### Post by vanadium on 2011-03-12
It is unclear from your question what partition you cannot access, neither how you are trying to access the partition. What is the error message?

There is an irregularity with your partition, but as your operating systems do start, this is not causing a practical issue. So do not further look into that issue.

You better show all the drives and the way partitions are currently mounted:
```

sudo fdisk -l
mount

```
Try to identify the one which is the problem and describe the issues you have trying to access the partition (including error messages).

---

### Post by oldfred on 2011-03-12
The not ending on cylinder boundary is actually good. Drives have not used CHS cylinders, heads, sectors since drives exceeded 8GB. They converted to LBA. 
New partitioning software rounds to 1Kib to match SSD, new 4K drives and flash drives. This only uses slightly more space than the old rounding, but now you may see tiny unallocated spaces in gparted.

The overlapping partitions is a problem. It looks like sda3 is inside the extended partition. By diffinition sda1-sda4 are primary partitions and cannot be inside an extended. It looks like sda3 should be sda9 or maybe to maintain order, sda8 and the current sda8 is sda9.

First backup partition table and copy backup to some other device.

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

There are several ways to fix this. Sometimes just reordering works or rereading in the PT.txt with sfdisk auto reorders. Since you may be changing partitions order, be prepared to reinstall grub and/or edit fstab. Most use UUID, so editing fstab may not be required.

 As with all partition problems make sure you have good backups of all you data as any partition changes can cause even bigger issues.

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)

If you are still in your system:
If not rebooted, use fdisk to manually recreate table posts by srs5694:
[http://ubuntuforums.org/showthread.php?t=1668247](http://ubuntuforums.org/showthread.php?t=1668247)

Forum member srs5694 has posted some instructions and has just mentioned  in another post a new tool to solve this issue. But it is still alpha,  says to use at your own risk and he may have a final by next week.

To convert a partition from primary to logical, at least one free  (unallocated) sector must exist between the partition and the one that  precedes it. 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Sometimes just using fdisk to rewrite partition table fixes it:
You can reorder the partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk

[]("http://www.rodsbooks.com/fixparts/")

---

### Post by fluo75 on 2011-03-12
> **vanadium said:**
> It is unclear from your question what partition you cannot access, neither how you are trying to access the partition. What is the error message?

There is an irregularity with your partition, but as your operating systems do start, this is not causing a practical issue. So do not further look into that issue.

You better show all the drives and the way partitions are currently mounted:
```

sudo fdisk -l
mount

```
Try to identify the one which is the problem and describe the issues you have trying to access the partition (including error messages).

Sorry, you are right this wasn't clear.
I only printed information about the hard-drive I can not access from KUbuntu (from KDE ou from the installation of KUBUNTU).
The message in KDE is "impossible to find a right partition on this partition)

Here is are more information (sorry, this is a little bit messy)

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount : type de système de fichiers «  » inconnu

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       204,799       202,752   7 HPFS/NTFS
/dev/sda2             208,845   605,264,939   605,056,095   f W95 Ext d (LBA)
/dev/sda5             210,893    25,382,699    25,171,807  83 Linux
/dev/sda6          25,382,763    32,756,534     7,373,772  83 Linux
/dev/sda7          32,772,096   307,202,047   274,429,952   7 HPFS/NTFS
/dev/sda8         602,614,278   605,264,939     2,650,662  82 Linux swap / Solaris
/dev/sda3         307,202,048   602,611,711   295,409,664   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 250.1 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres, total 488397168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   471,882,419   471,882,357   7 HPFS/NTFS
/dev/sdb2         471,883,774   488,396,799    16,513,026   5 Extended
/dev/sdb5         471,883,776   487,587,839    15,704,064  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 1000.2 Go, 1000204886016 octets
255 têtes, 63 secteurs/piste, 121601 cylindres, total 1953525168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,527,652,979 1,527,652,917  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   F009-64A5                              vfat                                     
/dev/sda1        7214F8ED14F8B4E7                       ntfs       System Reserved               
/dev/sda2: PTTYPE="dos" 
/dev/sda3        BA84094984090999                       ntfs                                     
/dev/sda6        07fe35b2-0118-4335-868d-da56c706ec95   ext4                                     
/dev/sda7        9898F31998F2F49A                       ntfs       New C Drive                   
/dev/sda8        0749c58f-3aed-4e98-8281-8152efe1b49d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AA84B93D84B90D37                       ntfs       DATA                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ce97c940-3036-4631-928a-947fdd68577b   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        be505a7a-092f-4169-9eeb-3a067bdc46b4   xfs        Video                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ce97c940-3036-4631-928a-947fdd68577b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set ce97c940-3036-4631-928a-947fdd68577b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7214f8ed14f8b4e7
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=ce97c940-3036-4631-928a-947fdd68577b /               ext4    errors=remount-ro 0       1
UUID=0749c58f-3aed-4e98-8281-8152efe1b49d	none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=f0f6ceff-d479-4c4f-a191-37a959ad7ffa none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 244.0GB: boot/grub/core.img
 244.9GB: boot/grub/grub.cfg
 244.8GB: boot/initrd.img-2.6.35-22-generic
 245.7GB: boot/initrd.img-2.6.35-23-generic
 247.9GB: boot/initrd.img-2.6.35-24-generic
 241.6GB: boot/initrd.img-2.6.35-25-generic
 249.1GB: boot/initrd.img-2.6.35-27-generic
 244.1GB: boot/vmlinuz-2.6.35-22-generic
 245.6GB: boot/vmlinuz-2.6.35-23-generic
 245.6GB: boot/vmlinuz-2.6.35-24-generic
 248.0GB: boot/vmlinuz-2.6.35-25-generic
 244.9GB: boot/vmlinuz-2.6.35-27-generic
 249.1GB: initrd.img
 241.6GB: initrd.img.old
 244.9GB: vmlinuz
 248.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  48 8b 74 24 40 48 83 c4  20 41 5c c3 cc cc cc cc  |H.t$@H.. A\.....|
00000010  cc cc cc cc cc cc cc cc  cc cc cc cc cc cc cc cc  |................|
00000020  48 89 5c 24 08 48 89 6c  24 10 48 89 74 24 18 48  |H.\$.H.l$.H.t$.H|
00000030  89 7c 24 20 41 54 48 83  ec 20 48 8b f2 ba 23 00  |.|$ ATH.. H...#.|
00000040  00 00 49 8b f9 49 8b d8  48 8b e9 e8 80 f1 ff ff  |..I..I..H.......|
00000050  44 8b 54 24 50 48 8b cb  4c 8b e0 44 89 50 08 e8  |D.T$PH..L..D.P..|
00000060  2c 8e 00 00 44 8b 5b 08  48 8b cf 45 89 5c 24 2c  |,...D.[.H..E.\$,|
00000070  e8 1b 8e 00 00 44 8b 5f  08 45 89 5c 24 30 80 bd  |.....D._.E.\$0..|
00000080  c0 04 00 00 00 74 04 33  c0 eb 08 8b 45 1c 41 2b  |.....t.3....E.A+|
00000090  44 24 04 48 8b 5c 24 30  48 8b 7c 24 48 89 46 10  |D$.H.\$0H.|$H.F.|
000000a0  48 89 2e 48 8b 6c 24 38  48 8b c6 c7 46 14 1c 00  |H..H.l$8H...F...|
000000b0  00 00 c7 46 08 ff ff ff  ff c7 46 0c 00 00 00 00  |...F......F.....|
000000c0  48 8b 74 24 40 48 83 c4  20 41 5c c3 cc cc cc cc  |H.t$@H.. A\.....|
000000d0  cc cc cc cc cc cc cc cc  cc cc cc cc cc cc cc cc  |................|
000000e0  48 89 5c 24 08 48 89 74  24 10 57 48 83 ec 50 48  |H.\$.H.t$.WH..PH|
000000f0  8b 01 48 8b f2 49 8b d8  48 8d 54 24 38 45 8b c1  |..H..I..H.T$8E..|
00000100  48 8b f9 ff 90 a0 00 00  00 33 c9 45 33 c0 48 89  |H........3.E3.H.|
00000110  4c 24 20 89 4c 24 2c 89  4c 24 30 48 8d 4c 24 20  |L$ .L$,.L$0H.L$ |
00000120  48 8b d0 c7 44 24 34 1d  00 00 00 c7 44 24 28 ff  |H...D$4.....D$(.|
00000130  ff ff ff e8 58 8c 00 00  4c 8b 1f 4c 8d 4c 24 20  |....X...L..L.L$ |
00000140  4c 8b c3 48 8b d6 48 8b  cf 41 ff 93 d0 00 00 00  |L..H..H..A......|
00000150  48 8b 5c 24 60 48 8b c6  48 8b 74 24 68 48 83 c4  |H.\$`H..H.t$hH..|
00000160  50 5f c3 cc cc cc cc cc  cc cc cc cc cc cc cc cc  |P_..............|
00000170  40 53 48 83 ec 30 4c 89  4c 24 20 4d 8b c8 41 b8  |@SH..0L.L$ M..A.|
00000180  7b 00 00 00 48 8b da e8  74 65 01 00 48 8b c3 48  |{...H...te..H..H|
00000190  83 c4 30 5b c3 cc cc cc  cc cc cc cc cc cc cc cc  |..0[............|
000001a0  40 53 48 83 ec 30 4c 89  4c 24 20 4d 8b c8 41 b8  |@SH..0L.L$ M..A.|
000001b0  7a 00 00 00 48 8b da e8  44 65 01 00 48 8b 00 20  |z...H...De..H.. |
000001c0  21 0d 83 fe bf 2b 00 08  00 00 5f 17 80 01 00 fe  |!....+...._.....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 65 72 28 00 00 00  |..........er(...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  c7 d2 98 d0 5a e3 2a 62  fd 28 57 11 c1 49 fd a6  |....Z.*b.(W..I..|
00000010  2d dd 98 33 2b 76 1d 6b  9d 4b 9b 88 1f 72 34 83  |-..3+v.k.K...r4.|
00000020  06 bd 75 d2 d7 cb 2b e6  45 f2 fb 8e 45 62 dc 69  |..u...+.E...Eb.i|
00000030  56 33 07 cc 91 02 dd 39  14 da 76 19 91 a7 ea 6a  |V3.....9..v....j|
00000040  e0 09 64 1f bd eb 9a eb  a0 10 18 0e c6 ce 39 15  |..d...........9.|
00000050  c0 5f 69 3e 50 0d 6f 22  30 1e 84 54 56 5a ac 96  |._i>P.o"0..TVZ..|
00000060  0c ab 34 b8 00 f7 23 a5  11 95 87 6b 9d c4 d6 49  |..4...#....k...I|
00000070  31 0c 17 04 56 3b 59 2e  d7 f2 ce d6 8c d6 c5 a6  |1...V;Y.........|
00000080  a7 6d 36 1f cd 8b 0b ee  29 26 6b 73 37 98 b3 c2  |.m6.....)&ks7...|
00000090  41 eb c8 ab 44 34 50 8c  b3 83 1b ee f9 85 67 f9  |A...D4P.......g.|
000000a0  65 43 27 19 04 8a e9 5d  ac e2 60 7c e8 b0 47 a8  |eC'....]..`|..G.|
000000b0  e2 a8 18 ed 0b 33 a4 f0  e1 ba f2 3a d0 05 7b 06  |.....3.....:..{.|
000000c0  47 90 43 2e d2 07 f2 a6  c9 0a db dd 4b 1a 9e 09  |G.C.........K...|
000000d0  c8 a6 c2 6d a1 95 c3 5c  c1 f5 c8 a7 5d 4b 6e 08  |...m...\....]Kn.|
000000e0  95 67 88 ed ea 72 31 eb  40 24 68 c6 15 4a 80 7a  |.g...r1.@$h..J.z|
000000f0  54 f2 22 2e 0a 67 27 15  97 6f a8 da bb 73 71 6c  |T."..g'..o...sql|
00000100  4f 4e a2 af c9 35 b2 ec  90 5c 43 f3 1c 1e 45 0c  |ON...5...\C...E.|
00000110  64 a4 03 80 1b 9e d5 98  b3 ba 5c 03 bc e0 f0 47  |d.........\....G|
00000120  bd 3a ee f2 da 24 12 1b  88 b8 3e a2 aa 43 71 6f  |.:...$....>..Cqo|
00000130  2c 8d 20 9a 03 cf a8 a1  09 9a b2 ba b0 05 71 cd  |,. ...........q.|
00000140  51 67 b9 2a ca 61 3c f4  c5 59 96 6b 47 40 52 e2  |Qg.*.a<..Y.kG@R.|
00000150  00 57 a8 c8 a9 52 ea 01  1a 1f 32 12 47 b8 a7 60  |.W...R....2.G..`|
00000160  45 05 b5 94 84 90 6e dc  71 57 25 47 68 c7 5f 93  |E.....n.qW%Gh._.|
00000170  ad 45 71 7b 6e 0e e3 34  63 04 0c 64 75 a9 4d e5  |.Eq{n..4c..du.M.|
00000180  b6 d6 fd fc 3d 0f 71 d2  93 01 15 e3 68 be 55 3c  |....=.q.....h.U<|
00000190  77 a8 84 91 00 dc f3 50  db 5f 58 aa bc 6d 3c 58  |w......P._X..m<X|
000001a0  93 91 92 2b 2c dd db c5  29 0d 34 18 fa 8a 94 33  |...+,...).4....3|
000001b0  41 9d 64 3c 82 31 53 5b  20 8b 7a b0 f9 65 00 fe  |A.d<.1S[ .z..e..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a0 ef 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by fluo75 on 2011-03-12
> **oldfred said:**
> The not ending on cylinder boundary is actually good. Drives have not used CHS cylinders, heads, sectors since drives exceeded 8GB. They converted to LBA. 
New partitioning software rounds to 1Kib to match SSD, new 4K drives and flash drives. This only uses slightly more space than the old rounding, but now you may see tiny unallocated spaces in gparted.
....


Sorry, I missed your reply. Thanks I will try that later... ;)

---

### Post by srs5694 on 2011-03-12
> **oldfred said:**
> The overlapping partitions is a problem. It looks like sda3 is inside the extended partition.
...
Forum member srs5694 has posted some instructions and has just mentioned  in another post a new tool to solve this issue. But it is still alpha,  says to use at your own risk and he may have a final by next week.

I've released a non-alpha version of the software; see [here](http://www.rodsbooks.com/fixparts/) for details. It is still very new, though, so oldfred's cautions about making backups should be heeded.

Other possible solutions might include using sfdisk and manually juggling partitions; using repair abilities in some other tool (I'm not aware of any that would solve this specific problem, but there may be something, particularly in the Windows world); or backing up data from /dev/sda3, deleting it, and re-creating it as a logical. Despite FixParts' newness, it's probably the safest option at this point, unless you're an expert at handling sfdisk's output or hear of some other more mature utility that can do the job.

Good luck!

---

### Post by fluo75 on 2011-03-12
> **srs5694 said:**
> I've released a non-alpha version of the software; see [here](http://www.rodsbooks.com/fixparts/) for details. It is still very new, though, so oldfred's cautions about making backups should be heeded.

Other possible solutions might include using sfdisk and manually juggling partitions;
...

Good luck!

Thanks for your message and these very interesting comments, I will try it tomorrow morning (it is 2am over here... :D )

I have to admit I am quite surprised by the quality of the comments on this forum!! :KS:KS:KS:KS

---

### Post by fluo75 on 2011-03-16
Hi,

I manage to backup the data, then I manage to move sda3 to sd9.
What was weird was that a linux partition moved also. I had to delete it (no problem since I was not using it anymore). I therefore deleted it and everything works well now.

Thank you very much!!!

Have a nice day!! ;)
David

---

