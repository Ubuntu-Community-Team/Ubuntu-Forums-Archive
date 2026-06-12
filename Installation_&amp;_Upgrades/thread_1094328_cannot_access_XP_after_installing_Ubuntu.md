---
title: "cannot access XP after installing Ubuntu"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Cthulhuvong on 2009-03-12
I just installed Ubuntu and it ran fine, but when I tried to boot XP up, I got a black screen which says "Starting up..." 

I followed the instructions in this thread since it seemed to be similar to my problem: [http://ubuntuforums.org/showthread.php?t=1074973](http://ubuntuforums.org/showthread.php?t=1074973)


> **caljohnsmith said:**
> OK, I think we should use "testdisk" to check if your Windows XP boot sector needs fixing; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda1 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the **"Extrapolated boot sector and current boot sector are different"**, then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

When I get to the bolded part, my computer gives me "Extrapolated boot sector and current boot sector are identical." 

And it gives me the options to Dump, List, or Quit.

Any help figuring out how to get it to run?

---

### Post by dstew on 2009-03-12
You should quit. The testdisk output means that there is no boot sector error.

Maybe you only have a mis-directed grub menu. Run your Ubuntu system, and open a terminal window. Enter the commands```
sudo fdisk -l
cat /boot/grub/menu.lst
```and post the results to the forum.

---

### Post by Cthulhuvong on 2009-03-12
Ok, so heres what I got:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1145cc10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22570   181293493+   7  HPFS/NTFS
/dev/sdb2           23203       24321     8981280    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb3           22571       23202     5076540    5  Extended
/dev/sdb5           22571       23168     4803403+  83  Linux
/dev/sdb6           23169       23202      273073+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c6645

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdh: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders
Units = cylinders of 342 * 512 = 175104 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              24       11534     1968128    b  W95 FAT32

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
# kopt=root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a17c9db0-6c68-4217-a86b-f5077e59518c

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
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Cthulhuvong on 2009-03-12
hate to bump this, but I really need some help here.

---

### Post by ranch hand on 2009-03-12
What do you get from runing terminal on your live CD with;
```

sudo grub

grub> geometry (hd1)

```
It looks to me that your bootable partition is sdb5. This would be (hd1,4) to grub.

---

### Post by IsmailBhai on 2009-03-12
you have 2 hard drives and two instances of XP? I see a media center and regular

---

### Post by dstew on 2009-03-12
At the grub menu, you can press 'c' to get a command line. Then you can enter```
geometry (hd1)
```This is I think a little better than using the Live CD, because it will show you which disk grub thinks is (hd1) in its native state. You can also do the same for (hd0).

It looks at first glance that it is set up correctly. So, maybe there is some confusion of disks with the BIOS.

---

### Post by ranch hand on 2009-03-12
I think that we need to know the geometry of sdb for sure.  I think that grub may be trying to boot from sda because of the bad influences it meets there.

It would be better to do this onboard.  I am not sure that he can do that at this time while I am sure that the live cd will get it.

It would be nice to run that same command on the other drive too.

---

### Post by Cthulhuvong on 2009-03-12
The regular is just PC Recovery, the Media Center is my XP. I get this when I type in geometry (hd1):

> grub> geometry (hd1)
drive 0x81: C/H/S = 24321/255/63, The number of sectors = 390721968, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is fat, partition type 0xc
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

---

### Post by ranch hand on 2009-03-12
OK, you note that this is hd1.  If I am not mistaken (very possible) XP wants to boot from sdg - hopefully (hd2).

I will admit to being baffled as to what to do here exactly.  It looks like the boot sector for XP is;
```

Device Boot Start End Blocks Id System
/dev/sdg1 1 91201 732572001 7 HPFS/NTFS

```
Is this in error?  Where the heck is sdg?  Why does it have a Win boot sector?

Did you by any chance run the other test that caljohnsmith suggested?
```

sudo bash ~/Desktop/boot_info_script*.sh

```
I would tell us if there is a problem with that XP boot sector.

---

### Post by Cthulhuvong on 2009-03-12
Says: 
> bash: /home/cthulhuvong/Desktop/boot_info_script*.sh: No such file or directory

---

### Post by ranch hand on 2009-03-12
Try this;
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt

```
It is from one of my threads when I broke grub pretty well.

---

### Post by Cthulhuvong on 2009-03-12
Heres the results 
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1145cc10

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   362,587,049   362,586,987   7 HPFS/NTFS
/dev/sdb2         372,753,360   390,715,919    17,962,560   c W95 FAT32 (LBA)
/dev/sdb3         362,587,050   372,740,129    10,153,080   5 Extended
/dev/sdb5         362,587,113   372,193,919     9,606,807  83 Linux
/dev/sdb6         372,193,983   372,740,129       546,147  82 Linux swap / Solaris


Drive sdh: _____________________________________________________________________

Disk /dev/sdh: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdh1               8,192     3,944,447     3,936,256   b W95 FAT32

/dev/sdh1 ends after the last cylinder of /dev/sdh

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D0B8EC7BB8EC6208" LABEL="DRV2_VOL1" TYPE="ntfs" 
/dev/sdb1: UUID="D4684B66684B4708" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sdb2: LABEL="PRESARIO_RP" UUID="4B6E-6BC0" TYPE="vfat" 
/dev/sdb5: UUID="a17c9db0-6c68-4217-a86b-f5077e59518c" TYPE="ext3" 
/dev/sdb6: UUID="9c07c27d-bcaa-4e63-88ae-00ca129b30f8" TYPE="swap" 
/dev/sdh1: UUID="50D6-C4B7" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/cthulhuvong/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cthulhuvong)
/dev/scd1 on /media/cdrom1 type udf (ro,nosuid,nodev,utf8,user=cthulhuvong)
/dev/sdh1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=cthulhuvong)

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sdb2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a17c9db0-6c68-4217-a86b-f5077e59518c

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
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a17c9db0-6c68-4217-a86b-f5077e59518c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a17c9db0-6c68-4217-a86b-f5077e59518c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=a17c9db0-6c68-4217-a86b-f5077e59518c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=9c07c27d-bcaa-4e63-88ae-00ca129b30f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 186.3GB: boot/grub/menu.lst
 186.3GB: boot/grub/stage2
 186.4GB: boot/initrd.img-2.6.27-11-generic
 186.4GB: boot/initrd.img-2.6.27-7-generic
 186.4GB: boot/vmlinuz-2.6.27-11-generic
 186.4GB: boot/vmlinuz-2.6.27-7-generic
 186.4GB: initrd.img
 186.4GB: initrd.img.old
 186.4GB: vmlinuz
 186.4GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

 sdc .
 sdd .
 sde .
 sdf .


---

### Post by ranch hand on 2009-03-12
OK, to my fairly inexperienced eye, everything looks pretty good.  For some reason your boot sector for XP won't mount.

This is a problem for me.  I ran 98 for 10 years and then jumped straight to Vista when the old comp died.  that lasted 3 weeks and from then on I have used Ubuntu.

Here is what I would do.  I would try to boot to your recovery partition.  If that boots up, maybe you can tweak things from there.  Wista useds that same system and I have tried to use it on the Dreaded Mother in Laws computer with no luck.

I would definately start by booting to recovery mode in Ubuntu and try any/all of the options there.  It actually seems to work on some things.

The problem is probably with the Ubuntu interaction with the XP boot sector, thus the fuse mount problem.

What you really need os to get caljohnsmith to peek in here, seems to know way more than is reasonable about grub and partitions, a real whiz.

If nothing else works you could just try reinstalling Ubuntu and see if it does a better job another time around.  There is a better way to do this than that.  Reinstallation is the incopitant persons last refuge, but that is where I am now.

I have several threads on grub saved because it seems like a very versitile and powerful tool.  It fasinates me.  I will see if I can find anything else.

---

### Post by Cthulhuvong on 2009-03-12
Thanks for the trying to help so far ranch hand. Hopefully someone will come along who knows what happened.

---

### Post by meierfra. on 2009-03-12
I agree with ranch hand  that every looks ok.  But here are a couple of things to try:


1) open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```


and add the following entries to the end of the file.

title Windows XP (rootnoverify)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Windows XP (no map)
rootnoverify (hd1,0)
chainloader +1

Save the file, reboot and try both.
If one of them works you can delete all other Windows entries from menu.lst.  If none of them works, report any error messages you got,


2)  Set you bios to boot from the Ubuntu drive. This should allow you to boot directly into XP.  Is that true? If not, report any error messages.

Also it looks like  XP is on the same hard drive as Ubuntu. Is that true?

---

### Post by IsmailBhai on 2009-03-13
i would insert XP cd and repair MBR. Then reinstall grub.

---

### Post by Cthulhuvong on 2009-03-13
I tried using the rootnoverify and no map stuff and now I get a black screen every time I try to start up my computer. I can't boot at all. Any advice?

---

### Post by meierfra. on 2009-03-13
How early do you get the black screen?  Does the Bios screen show up first?  Are you able to enter the Bios Setup and change the boot order?  Does the Grub menu appear? Are you able to boot from the Ubuntu LiveCD?

---

### Post by Cthulhuvong on 2009-03-13
I get it right away, no bios screen, no nothing. No grub menu. No, I cannot boot from the CD.

---

### Post by meierfra. on 2009-03-13
Sounds like a serious hardware problem.  Sorry, I don't know much about hardware,so I won't be able to help you with that.  I suggest to start a new thread with a new title.

---

### Post by ranch hand on 2009-03-13
So, (1) you start the computer (2) you get a black screen and (3) can't boot from CD.

Is this correct?  No flash of the Manufactures logo (or MB manufactures logo if you built it yourself).

If this is the case it is not likely to be caused by any OS or software.  This sounds, very unpleasantly, like a MB or CPU problem.  I would check your video card and make sure that the cooling fan on it is working and check all connections invoved with it.

I assume that there is nothing wrong with your monitor.  You may want to try another if you have one available.

This could be the root of your boot problems.  You were booting to Ubuntu.  You changed nothing on the /boot/grub/menu.lst that had to do with Ubuntu.  I don't care what you did to the rest of the boot options, Ubuntu should work.

---

### Post by ranch hand on 2009-03-13
I would urgently suggest that you pull any active HDDs from that box and do any recovery attempts with a blank slate or one with Ubuntu installed on a simular system.

You have data you may want to save and leaving it in that box puts in in great danger of being fried.

---

### Post by meierfra. on 2009-03-13
Cthulhuvong has started a new [thread]("http://ubuntuforums.org/showthread.php?t=1095303")

---

### Post by ranch hand on 2009-03-13
This is the only thread that comes up an a search for Cthulhuvong.

---

### Post by meierfra. on 2009-03-13
ranch hand:  click on the link in my previous post.

Also if you click on "Cthulhuvong"   (on the left side of his/her post) and then select "Find more post by Cthulhuvong" you will find all of his/her recent posts.

---

### Post by ranch hand on 2009-03-13
I never new about clicking on the usernames.   That is really neat, thanks.

There is always something new to learn for us cranky old geezers.

---

