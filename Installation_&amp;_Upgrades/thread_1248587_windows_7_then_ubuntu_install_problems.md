---
title: "windows 7 then ubuntu install problems"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by jumblepod on 2009-08-24
Through the the uni i go to they give us subscription to msdn which through i obtained a full copy of windows 7 pro 64bit. I thought it was about time to upgrade from xp. My current set up at the time was xp and ubuntu dual booting using the grub loader. i thought it was time for a fresh start so I formatted the whole hard drive. I then proceeded to install windows 7, after which i install all my programs and everything back to normal like my xp installation was. I then decided to put ubuntu on so i created some unallocated free space of 30gb using the disk tool in windows 7 i then put in the cd restarted my computer and booted up the ubuntu installation. When it got to the formatting tools part of the installation where you say where you want to install it i selected use largest continuous free space i then pressed next and waited for the installation to complete. It finished and the computer restarted i then noticed there wasnt any grub menu appearing or any boot manager menu for that matter. It just loaded up windows 7. I restarted the computer to see if i could have missed it and it did the same again. For some reason it wont install or use the grub boot manager. So i thought something may have gone wrong with the installtion of ubuntu so i have installed it again the same as before. Again no boot menu it just loads up windows 7. Anyone know why ubuntu isnt installing the grub boot menu or is windows 7 stopping it some how i had no issuses with xp and ubuntu dual boot. Its not like im trying to install ubuntu then windows 7. It should be easy this way round!!!!  remember i am using an actual version of windows 7 pro 64bit not a beta or rc one.

Sorry this is a long winded explaination i thought it would be necessary to explain in full.

---

### Post by dstew on 2009-08-24
Boot the Live CD, and see if you can verify that Ubuntu was installed to a new partition. The command ```
sudo fdisk -l
```will at least show you if the Linux file system is there. Post the output of the command to the forum so we can verify the disk partition structure.

If the Linux file system is there, try to mount it and see if there is a /boot/grub/menu.lst file in the hard-disk installation. If so, see if you can open the file with a text editor. Make sure you are looking at the file on the hard disk, not on the CD. Post the file contents to the forum.

As far as Windows protecting the MBR, and not allowing it to be overwritten, it would need to have this implemented in the BIOS, since the MBR is read by the BIOS before the operating system gets loaded. And, Windows could not have protected the MBR during your installation attempt, since when the Ubuntu CD is booted, it is the only operating system. Check your BIOS to see if it has some feature that protects the MBR of the boot disk.

---

### Post by jumblepod on 2009-08-24
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d261d25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d261d26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea5bea5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13       26485   212635345+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdc3           26486       30401    31449600    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdc5           26486       30234    30103888+  83  Linux
/dev/sdc6           30234       30401     1345648+  82  Linux swap / Solaris


i have tryed gedit /boot/grub/menu.1st and its blank.

---

### Post by philcamlin on 2009-08-24
> **jumblepod said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d261d25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d261d26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea5bea5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13       26485   212635345+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdc3           26486       30401    31449600    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdc5           26486       30234    30103888+  83  Linux
/dev/sdc6           30234       30401     1345648+  82  Linux swap / Solaris


i have tryed gedit /boot/grub/menu.1st and its blank.

you have to have a menu.lst did you open it with text editor?

---

### Post by raymondh on 2009-08-24
> **jumblepod said:**
> ubuntu@ubuntu:~$ 

i have tryed gedit /boot/grub/menu.1st and its blank.

```
gksudo gedit /boot/grub/menu.lst
```

small L not 1 not I.

---

### Post by jumblepod on 2009-08-24
gksudo gedit /boot/grub/menu.lst
 this is what i typed and its a blank document

---

### Post by jumblepod on 2009-08-24
I found it now i was trying to find it through the live cd files instead of the partition my installed linux is on.

ive opened it and theres loads of stuff in it.

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
# kopt=root=UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c36413f-c3ff-4d3a-9c44-843b61b4d566

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
uuid        8c36413f-c3ff-4d3a-9c44-843b61b4d566
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8c36413f-c3ff-4d3a-9c44-843b61b4d566
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8c36413f-c3ff-4d3a-9c44-843b61b4d566
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

---

### Post by presence1960 on 2009-08-24
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jumblepod on 2009-08-24
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d261d25

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d261d26

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea5bea5b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   425,477,538   425,270,691   7 HPFS/NTFS
/dev/sdc3         425,491,920   488,391,119    62,899,200   5 Extended
/dev/sdc5         425,491,983   485,699,759    60,207,777  83 Linux
/dev/sdc6         485,699,823   488,391,119     2,691,297  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="56ECE5F7ECE5D0F3" LABEL="Media" TYPE="ntfs" 
/dev/sdb1: UUID="CC8014DB8014CE38" LABEL="Software" TYPE="ntfs" 
/dev/sdc1: UUID="4E68E6F168E6D6AD" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc2: UUID="A430EA2030E9F8E6" TYPE="ntfs" 
/dev/sdc5: UUID="8c36413f-c3ff-4d3a-9c44-843b61b4d566" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc6: TYPE="swap" UUID="0c78d4b1-55db-43f7-82ad-36e1cc54840d" 

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


=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c36413f-c3ff-4d3a-9c44-843b61b4d566

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
uuid        8c36413f-c3ff-4d3a-9c44-843b61b4d566
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8c36413f-c3ff-4d3a-9c44-843b61b4d566
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8c36413f-c3ff-4d3a-9c44-843b61b4d566
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=8c36413f-c3ff-4d3a-9c44-843b61b4d566 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=0c78d4b1-55db-43f7-82ad-36e1cc54840d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 242.8GB: boot/grub/menu.lst
 242.8GB: boot/grub/stage2
 242.8GB: boot/initrd.img-2.6.28-11-generic
 242.9GB: boot/vmlinuz-2.6.28-11-generic
 242.8GB: initrd.img
 242.9GB: vmlinuz

---

### Post by presence1960 on 2009-08-24
simple fix do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd2,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd2,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd2)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Reboot and then go into BIOS and set sdc (250GB) as first in boot order of hard disks. This will bring up GRUB when you boot. Choose Ubuntu when GRUB comes up. Then open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```

Change this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Windows Vista (loader)
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

```
to :
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title         Windows 7 (loader)
rootnoverify  (hd2,0)
chainloader   +1

```

click save on the toolbar and close that file. reboot & try booting into windows 7 when GRUB appears.

---

### Post by jumblepod on 2009-08-24
thank you so much it worked. Did this problem occur because im using 3 hard drives. Could you explain to me why it didnt just work when i installed linux like it has many times in the past when ive installed it and had no problem with the grub loader.

---

### Post by presence1960 on 2009-08-24
> **jumblepod said:**
> thank you so much it worked. Did this problem occur because im using 3 hard drives. Could you explain to me why it didnt just work when i installed linux like it has many times in the past when ive installed it and had no problem with the grub loader.

The problem is that GRUB was installed to sda but sda was not set as first boot in BIOS. So when your machine booted GRUB did not take over. Since a windows bootloader did either sdb or sdc was booting first. I find it better if Ubuntu and windows are installed on the same hard disk to keep GRUB on that disk.

A bootloader can only do it's job if it is on the MBR of the first hard disk that boots. Or if it is installed to the first sector of the partition of that OS and chainloaded from the GRUB on MBR.

When you try to boot Windows 7 you may need to change the windows 7 entry to this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title         Windows 7 (loader)
rootnoverify  (hd0,0)
chainloader   +1
```

Because sdc is now the first booting hard disk it is actually (hd0). Sometimes Ubuntu reads the order of disks differently than BIOS. When entering (hdx,y) in GRUB it is the order in BIOS that is required. When you get a chance try to boot windows 7 from GRUB and see if it works. if it does not just edit menu.lst to the above.

---

