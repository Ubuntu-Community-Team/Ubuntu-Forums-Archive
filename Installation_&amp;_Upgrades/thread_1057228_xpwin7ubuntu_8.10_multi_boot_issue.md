---
title: "xp/win7/ubuntu 8.10 multi boot issue"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by shadowmastr on 2009-02-01
I've been looking thru the posts here and haven't seen one particular to my issue.

I have 2 - 1 terabyte drives in my system. I have been dual booting into xp and windows 7 beta since the win7 was publicly available. I made 4 partitions on the first disk drive, a 50 gig for xp OS, 50 gig for win7 OS, and split the rest into 2 other partitions, one for programs, other for downloads, music, video, etc. With the win7 bootloader, whichever windows os I selected to boot from, it would make that the c drive, the other os the d drive, and arrange the others as it saw fit. Using the nifty feature in windows to rename drives/partitions, I let windows manage the c and d switching, and I renamed the others to be consistant with each of the 2 OS's.

The second drive was mostly sitting there, I split it into 2 partitions, one had more music and videos, the other empty.

I decided to install ubuntu 8.10. I was going to replace the win7 with ubuntu, but wanted more space than the 50 gigs set aside for the win7 os partition. So I installed ubuntu on the last partition of the second drive, with like 450 gigs free or so. I made a separate / partition, a separate /home partition, and a separate /swap partition, all formatted with ext3.

All is well with the ubuntu installation. I get the grub loader with the choice of ubuntu or windows vista/longhorn (as it named itself), no xp listed. I figured that would be under the vista loader.

Ubuntu loads and runs fine. Here's the problem. When I select the Vista loader, it comes back with an error 29, diskwrite error, and won't load anything windows, just hit enter to return to grub loader screen.

I NEED to get back into xp, unfortunately I have a few programs I use to work from home that ONLY work with 32 bit xp. Hopefully just a bit of tweaking to the loader or something can get me loading windows again?? 

I'd hate to have to reinstall xp, it's not a hassle, but reinstalling all the programs I need again gets old, plus that'll probably break the grub loader and I'd lose ubuntu too?? Don't really care about the win7, and since I did just install ubuntu, could always do that again as well. Sure would be nice to have the tri-boot like it's supposed to though...

Any and all help will be greatfully appreciated.... thanks....

---

### Post by shadowmastr on 2009-02-01
I've seen a number of requests in other posts for info from the bootinfo script, so here is mine:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6754acd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,859,647   104,857,600   7 HPFS/NTFS
/dev/sda2         104,859,648   209,717,247   104,857,600   7 HPFS/NTFS
/dev/sda3         209,717,248   838,862,847   629,145,600   7 HPFS/NTFS
/dev/sda4         838,862,848 1,953,521,663 1,114,658,816   7 HPFS/NTFS

/dev/sda4 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa51a89ea

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,027,606,527 1,027,604,480   7 HPFS/NTFS
/dev/sdb2       1,027,606,528 1,227,606,527   200,000,000  83 Linux
/dev/sdb3       1,903,525,785 1,953,520,064    49,994,280  83 Linux
/dev/sdb4       1,883,508,795 1,903,525,784    20,016,990   5 Extended
/dev/sdb5       1,883,524,860 1,903,525,784    20,000,925  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________


/dev/sda1: UUID="60100B5F100B3B92" LABEL="XP" TYPE="ntfs" 
/dev/sda2: UUID="EEF20E18F20DE625" LABEL="OS_2" TYPE="ntfs" 
/dev/sda3: UUID="9A92FF9C92FF7AD9" LABEL="Programs" TYPE="ntfs" 
/dev/sda4: UUID="921A01F11A01D361" LABEL="Entertainment" TYPE="ntfs" 
/dev/sdb1: UUID="083E31BA3E31A19C" LABEL="Disk2A" TYPE="ntfs" 
/dev/sdb2: UUID="4de041ee-c35f-45a8-bc89-cf8a4e37e459" TYPE="ext3" 
/dev/sdb3: UUID="357e1578-80a8-4a01-a353-be21e3c292ff" TYPE="ext3" 
/dev/sdb5: UUID="fe2733aa-3b67-4c08-a1d8-7fe7cf0639c0" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)
/dev/sda1 on /media/XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/OS_2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdb3/boot/grub/menu.lst: ===========================

default 0
timeout 10

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
# kopt=root=UUID=357e1578-80a8-4a01-a353-be21e3c292ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=357e1578-80a8-4a01-a353-be21e3c292ff

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

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=357e1578-80a8-4a01-a353-be21e3c292ff ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=357e1578-80a8-4a01-a353-be21e3c292ff ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=357e1578-80a8-4a01-a353-be21e3c292ff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=4de041ee-c35f-45a8-bc89-cf8a4e37e459 /home           ext3    relatime        0       2
# /dev/sdb5
UUID=fe2733aa-3b67-4c08-a1d8-7fe7cf0639c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 987.9GB: boot/grub/menu.lst
 987.9GB: boot/grub/stage2
 988.0GB: boot/initrd.img-2.6.27-11-generic
 987.9GB: boot/initrd.img-2.6.27-7-generic
 987.9GB: boot/vmlinuz-2.6.27-11-generic
 987.9GB: boot/vmlinuz-2.6.27-7-generic
 988.0GB: initrd.img
 987.9GB: initrd.img.old
 987.9GB: vmlinuz
 987.9GB: vmlinuz.old
```

hope this helps with a quicker informed response. Thanks again...

---

### Post by Pumalite on 2009-02-01
You can boot any of them with Super Grub.
For the time being; post:
```
sudo fdisk -lu
```

---

### Post by shadowmastr on 2009-02-01
ok, here are the results from the flist command:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6754acd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104859647    52428800    7  HPFS/NTFS
/dev/sda2       104859648   209717247    52428800    7  HPFS/NTFS
/dev/sda3       209717248   838862847   314572800    7  HPFS/NTFS
/dev/sda4       838862848  1953521663   557329408    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa51a89ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1027606527   513802240    7  HPFS/NTFS
/dev/sdb2      1027606528  1227606527   100000000   83  Linux
/dev/sdb3      1903525785  1953520064    24997140   83  Linux
/dev/sdb4      1883508795  1903525784    10008495    5  Extended
/dev/sdb5      1883524860  1903525784    10000462+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Pumalite on 2009-02-01
Post:
```
cat /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2009-02-01
How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP/Vista
root (hd0,0)
chainloader +1
```
In other words, I would recommend getting rid of the "savedefault" line, because that may be why you are getting a Grub error 29. Let me know if that works or not.

---

### Post by shadowmastr on 2009-02-01
ok here is that result:

```
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
# kopt=root=UUID=357e1578-80a8-4a01-a353-be21e3c292ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=357e1578-80a8-4a01-a353-be21e3c292ff

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

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=357e1578-80a8-4a01-a353-be21e3c292ff ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=357e1578-80a8-4a01-a353-be21e3c292ff ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive
```

In going thru the previous result, I tried changing the root for the vista loader to (hd1.0), still got the error 29 diskwrite error....

---

### Post by Pumalite on 2009-02-01
Map your entry for Windows

---

### Post by shadowmastr on 2009-02-01
> **caljohnsmith said:**
> How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP/Vista
root (hd0,0)
chainloader +1
```
In other words, I would recommend getting rid of the "savedefault" line, because that may be why you are getting a Grub error 29. Let me know if that works or not.

removing the savedefault line did it! It now will let me load both crappy versions of windoze!!!

I really wish I could get off the windoze teat, but as mentioned earlier, a couple programs I need to use for work are 32 bit xp only, won't work with 64 bit anything, and no linux either.

Plus I do have a gaming jones goin... can't do the lotro, guitar hero, deadspace kinda things on the linux... as far as I know.... yet....

Thanks caljohnsmith!! and also Pumalite for the assistance..... I can use the windoze for work, and gaming, and the ubuntu for the rest... soon as I can figure out why totem tells me it can't access my resources when I put in a dvd or cd, but thats for a different post if I can't figure it out....

---

### Post by caljohnsmith on 2009-02-01
Glad that worked OK, shadowmastr; cheers and enjoy your Windows gaming and your Ubuntu install. :)

---

