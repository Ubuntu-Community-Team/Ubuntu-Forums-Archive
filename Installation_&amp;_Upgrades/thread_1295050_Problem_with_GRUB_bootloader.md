---
title: "Problem with GRUB bootloader"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by kphanee on 2009-10-19
Hi,
I am facing a strange problem with GRUB boot loader. I recently took a 1TB hard disk in addition to my earlier 160GB hard disk. I installed Ubuntu Jaunty on my 160GB hard disk and Window XP SP2 on the 1TB hard disk. 

But grub in not loading the boot loader by default when I boot my system. It comes to grub command prompt and stops. When I try to give any command from command prompt, it doesn't execute but gives error about not finding any OS images in the disk. 

But, if I keep any disk in the DVD drive, then grub is properly loading the boot loader. Further, it loads the selected OS also properly. I have checked grub configuration file also and it is correct. Even when I try to do grub-install (command: grub-install /dev/sda) again from ubuntu, it fails saying no valid OS images found to be installed.

One observation that I have seen is, when grub is failing, its going to GRUB stage 2 loading & failing. When the grub is loading the boot loader correctly, its loading from grub stage 1.5.

Please help me out on this problem. Let me know if any logs are required. Below is the current configuration of my system. 

BIOS configuration:
Master Channel 0: DVD Drive
Master Channel 1: 1TB SATA HDD (/dev/sda)
Master Channel 2: 160GB SATA HDD (/dev/sdb)

Windows installed on : /dev/sda1
Jaunty installed on : /dev/sdb1
GRUB boot loader installed on : /dev/sda

Partitions on HDD: 
/dev/sda
/dev/sda1 - NTFS Primary
/dev/sda2 - Extended
/dev/sda5 - NTFS Logical
/dev/sda6 - NTFS Logical
/dev/sda7 - NTFS Logical

/dev/sdb
/dev/sdb1 - ext4 /
/dev/sdb2 - ext4 /home
/dev/sdb3 - Linux swap
/dev/sdb4 - ext4 /scratchbox


Thanks in advance,
Ravi

---

### Post by arrange on 2009-10-19
Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")?

([how to run the script]("http://sourceforge.net/docman/display_doc.php?docid=137292&group_id=250055"))

---

### Post by kphanee on 2009-10-19
The output of the boot_info_script032.sh script as requested:


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks at sector 50251113 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #7 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbc3581d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   419,441,084   419,441,022   7 HPFS/NTFS
/dev/sda2         419,441,085 1,953,520,064 1,534,078,980   5 Extended
/dev/sda5         419,441,148 1,048,610,744   629,169,597   7 HPFS/NTFS
/dev/sda6       1,048,610,808 1,677,780,404   629,169,597   7 HPFS/NTFS
/dev/sda7       1,677,780,468 1,953,520,064   275,739,597   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x32543254

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   301,266,944   301,266,882  83 Linux
/dev/sdb2         301,266,945   312,576,704    11,309,760   5 Extended
/dev/sdb5         301,267,008   312,576,704    11,309,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7684E8C784E88B47" LABEL="WinPrimary" TYPE="ntfs" 
/dev/sda5: UUID="9EF0E5ACF0E58ABB" LABEL="WinData" TYPE="ntfs" 
/dev/sda6: UUID="7E48E60D48E5C3CD" LABEL="WinMovies" TYPE="ntfs" 
/dev/sda7: UUID="E00C355B0C352E42" LABEL="WinShare" TYPE="ntfs" 
/dev/sdb1: UUID="15a6be23-e632-4262-b8dc-f0ace75bea82" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="ddac569a-e7eb-429f-a4e2-d9020c6812dc" 

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
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kphanee/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kphanee)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=kphanee)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

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
# kopt=root=UUID=15a6be23-e632-4262-b8dc-f0ace75bea82 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=15a6be23-e632-4262-b8dc-f0ace75bea82

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
uuid        15a6be23-e632-4262-b8dc-f0ace75bea82
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=15a6be23-e632-4262-b8dc-f0ace75bea82 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        15a6be23-e632-4262-b8dc-f0ace75bea82
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=15a6be23-e632-4262-b8dc-f0ace75bea82 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        15a6be23-e632-4262-b8dc-f0ace75bea82
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
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
UUID=15a6be23-e632-4262-b8dc-f0ace75bea82 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ddac569a-e7eb-429f-a4e2-d9020c6812dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  12.6GB: boot/grub/menu.lst
  12.6GB: boot/grub/stage2
  12.7GB: boot/initrd.img-2.6.28-11-generic
  12.7GB: boot/vmlinuz-2.6.28-11-generic
  12.7GB: initrd.img
  12.7GB: vmlinuz

---

### Post by bulldog on 2009-10-19
You have GRUB installed on both hdd's if I'm not mistaken.
Try to boot from the 'old hdd' and see what it gives.
In my opinion it should boot your ubuntu but probably not your windows.
This is no problem,we can fix this in a few minutes.
Just boot from the original hdd with ubuntu and tell me what happens.

---

### Post by arrange on 2009-10-19
I would change the boot priority so that it boots from *sdb* first (not *sda*) and install grub on it (from Ubuntu):```
sudo grub-install /dev/sdb
```

---

### Post by kphanee on 2009-10-19
I am not sure what you meant by boot from 'old hdd', but if you meant booting from the disk on which ubuntu is installed, then only ubuntu should be booted, because it doesn't have any other OS. The windows is present on first hdd. From what I understood, both the solutions suggested point to the same I guess i.e. installing grub on sdb & check the result. 

I would try that and come back with the result.

Thanks,
Ravi

---

### Post by kphanee on 2009-10-19
Thanks. Installing GRUB boot loader on /dev/sdb solved the problem. Thanks again.

---

### Post by kphanee on 2009-10-20
Sorry, I didn't check completely before posting last reply. After installing GRUB to /dev/sdb, now the boot loader is getting loaded correctly, but if the loading of Windows is failing. 

When I select the Windows OS, it gives an error something like
13: incorrect or unexecutable format image.

---

### Post by arrange on 2009-10-20
Could you post an updated RESULTS.txt again?

---

### Post by presence1960 on 2009-10-20
> **kphanee said:**
> Sorry, I didn't check completely before posting last reply. After installing GRUB to /dev/sdb, now the boot loader is getting loaded correctly, but if the loading of Windows is failing. 

When I select the Windows OS, it gives an error something like
13: incorrect or unexecutable format image.
Now that you are booting from sdb first in BIOS that has become (hd0) and sda has become (hd1).

Boot into Ubuntu & open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to windows entry at bottom and change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title          Microsoft Windows XP Professional
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

```

When using (hdx,y) in GRUB it is the order of hard disk booting in BIOS which determines the x designation, not sda, sdb, sdc etc. because that is the order in which the hard disks come on when you boot.

So sdb boot first so it is (hd0) so it becomes (hd0,y) where y = the partition number ( which BTW counting for partitions starts at 0 also) So the first partition on sdb in GRUB is (hd0,0) on your machine

---

### Post by bulldog on 2009-10-20
Opem your menu.lst```
gksu gedit /boot/grub/menu.lst
```

Look at the bottom of the menu.lst if there's an entry for windows like this.
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1

If so make it like this and if not copy paste all of this to the bootom of your menu.lst.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader +1

Safe the menu.lst and try again.

---

### Post by limpopokanoah on 2009-10-20
I am having a similar problem.  I have Ubuntu 9.04 installed directly to a 8G usb stick using the alternate installation iso.  Everything went quite well. I have grub installed on the usb wich in this case is sdb, but after i choose to boot ubuntu from the grub menu the first text that pops up is that it is searching (hd0,0) when i know from reading 9 pages back and running 

   sudo find /boot/grub/stage2

that my location is (hd1,0).  From reading a few of these i have anticipated your first quetion and yes i have the results.txt

```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 10993727 of the same hard drive for 
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

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd1 has 
                       976765094 sectors.. But according to the info from the 
                       partition table , it has 976768002 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7f2bdd3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   957,939,884   957,939,822   7 HPFS/NTFS
/dev/sda2         957,939,885   976,768,064    18,828,180   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004aea0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    14,924,384    14,924,322  83 Linux
/dev/sdb2          14,924,385    15,695,504       771,120   5 Extended
/dev/sdb5          14,924,448    15,695,504       771,057  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ba0e9c1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdc5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce342d02

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7AD2F220D2F1E075" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="745761e9-2b86-454e-bdfc-26d10cfb6a02" TYPE="ext3" 
/dev/sdb5: UUID="df4c58c7-6b45-4702-88c8-b8a5df1149f1" TYPE="swap" 
/dev/sdc5: UUID="84002C3C002C3796" LABEL="HP Personal Media Drive" TYPE="ntfs" 
/dev/sdd1: UUID="000A-605F" TYPE="vfat" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdd1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc5 on /media/HP Personal Media Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=745761e9-2b86-454e-bdfc-26d10cfb6a02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=745761e9-2b86-454e-bdfc-26d10cfb6a02

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
uuid        745761e9-2b86-454e-bdfc-26d10cfb6a02
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=745761e9-2b86-454e-bdfc-26d10cfb6a02 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        745761e9-2b86-454e-bdfc-26d10cfb6a02
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=745761e9-2b86-454e-bdfc-26d10cfb6a02 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

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
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
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
# / was on /dev/sdc1 during installation
UUID=745761e9-2b86-454e-bdfc-26d10cfb6a02 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=df4c58c7-6b45-4702-88c8-b8a5df1149f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   5.5GB: boot/grub/menu.lst
   5.6GB: boot/grub/stage2
   5.5GB: boot/initrd.img-2.6.28-11-generic
   5.5GB: boot/vmlinuz-2.6.28-11-generic
   5.5GB: initrd.img
   5.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 27 90 50 43 43 4c 4f  4e 45 20 00 00 00 00 00  |.'.PCCLONE .....|
00000010  00 e5 40 38 3a 00 00 00  00 1a b2 9f f7 00 00 4c  |..@8:..........L|
00000020  6f 61 64 20 45 72 72 6f  72 fc 33 c0 8e d8 a0 19  |oad Error.3.....|
00000030  7c 48 d1 e8 40 40 e8 4a  00 e8 68 00 72 10 e8 ba  ||H..@@.J..h.r...|
00000040  00 3b 06 1b 7c 75 07 e8  09 00 ff 2e 0d 7c e8 13  |.;..|u.......|..|
00000050  00 eb fe a1 0b 7c 26 a3  0b 00 c3 81 c6 00 7c a4  |.....|&.......|.|
00000060  47 e2 fc c3 b8 03 00 cd  10 bf 00 b8 8e c7 33 ff  |G.............3.|
00000070  be 03 00 b9 08 00 e8 e2  ff be 1f 00 b9 0a 00 e8  |................|
00000080  d9 ff c3 33 c9 89 0e 0d  7c 8e c1 bb 13 04 26 8b  |...3....|.....&.|
00000090  0f 89 0e 0b 7c 2b c8 26  89 0f c1 e1 06 8e c1 89  |....|+.&........|
000000a0  0e 0f 7c c3 1e 8a 0e 19  7c b5 00 c1 e1 09 8b f9  |..|.....|.......|
000000b0  b0 00 57 b9 10 00 f3 aa  5f b0 10 26 88 05 a0 19  |..W....._..&....|
000000c0  7c 26 88 45 02 8c c0 26  89 45 06 33 c0 26 89 45  ||&.E...&.E.3.&.E|
000000d0  04 a1 11 7c 26 89 45 08  a1 13 7c 26 89 45 0a a1  |...|&.E...|&.E..|
000000e0  15 7c 26 89 45 0c a1 17  7c 26 89 45 0e 8b f7 8c  |.|&.E...|&.E....|
000000f0  c0 8e d8 b2 80 b4 42 cd  13 1f c3 8a 0e 19 7c b5  |......B.......|.|
00000100  00 c1 e1 08 1e ba 00 00  a1 0f 7c 8b 36 0d 7c 8e  |..........|.6.|.|
00000110  d8 ad 33 d0 e2 fb 1f 8b  c2 c3 61 73 0e 4f 74 0b  |..3.......as.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 2c 44 63  02 2d 34 ce 00 00 80 01  |.....,Dc.-4.....|
000001c0  01 00 0c fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```I think i need to do the re-routing that was suggested a few posts back, but i was curious if my case was any different before i did something i wasn't sure of. Thanks for any help.
                                              Thomas

edit: Everything is fine when i don't have my usb plugged in (windows boots fine) and i haven't tried booting into windows thru the usb because i didn't feel the need, but i might try now to see what happens.

edit2: I forgot to mention that I had tried to re-route either windows or linux, but from my ubuntu live cd when i bring up the terminal and type ```
gksudo gedit /boot/grub/menu.lst
``` gedit opens up an empty file.

---

### Post by limpopokanoah on 2009-10-20
Ok, so now i have tried to boot into vista using the usb.  Grub takes me to the Starting up...   prompt and sticks.  When i try to boot into Ubuntu it says     Boot from: (hd0,0) ext3 and a long uuid i believe.  Then it tells me i have fatal errors because it can't load the kernel modules, and i think this is due to it looking in the wrong place...

---

### Post by presence1960 on 2009-10-20
> **limpopokanoah said:**
> Ok, so now i have tried to boot into vista using the usb.  Grub takes me to the Starting up...   prompt and sticks.  When i try to boot into Ubuntu it says     Boot from: (hd0,0) ext3 and a long uuid i believe.  Then it tells me i have fatal errors because it can't load the kernel modules, and i think this is due to it looking in the wrong place...

Actually your Ubuntu is (hd0,0) because when you boot from the USB it is the first disk in the boot order which makes it (hd0). Ubuntu is on sdb1 which is the first partition which then makes ubuntu (hd0,0).

Let me fill you in on a little secret about GRUB and Ubuntu/fdisk. They read the order of disks differently. Ubuntu & fdisk have their own way of assigning disk order which we see as sda, sdb, sdc, etc.

But when using (hdx,y) in GRUB it is the order of the hard disk booting in BIOS which determines the x designation in (hdx,y). x = hard disk, y = partition- counting starts at 0 for both. Why does BIOS determine the x designation even though Ubuntu/fdisk report a different order? That is simple, if you consider what happens when you boot your computer. The hard disk boot order in BIOS determines which hard disks are looked at to boot in which order. In your case even though Ubuntu/fdisk list sda as the first disk, when you boot your USB flash disk that is actually the first disk looked at to boot which makes it (hd0) in spite of Ubuntu's/fdisk's labeling that flash disk as sdb.

In conclusion your GRUB looks correct to me and those errors are why you can't boot, they are kernel errors not GRUB errors.. I would try reinstalling Ubuntu onto the flash drive again and keep GRUB in the same place.

To get Vista to boot from GRUB you need to go into your BIOS and see which position sda boots (second, third or fourth) and change the Vista entries to correspond to the order of your sda disk booting. I will use x to designate where you should change:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista (loader)
rootnoverify    (hdx,0)
map             (hd0) (hdx)
map             (hdx) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista Recovery
rootnoverify    (hdx,1)
map             (hd0) (hdx)
map             (hdx) (hd0)
chainloader     +1


```

Example: if sda boots second in BIOS x=1
         if sda boots third in BIOS x=2
         if sda boots fourth in BIOS x=3

---

### Post by kphanee on 2009-10-21
Thanks for the help. After mapping the hd0 -> hd1 & vice versa in menu.lst, both the partitions are working now properly. Thanks for all the help. :)

---

