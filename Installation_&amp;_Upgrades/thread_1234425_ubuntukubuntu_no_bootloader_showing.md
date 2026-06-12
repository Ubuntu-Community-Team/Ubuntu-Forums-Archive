---
title: "ubuntu/kubuntu no bootloader showing"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by clownz on 2009-08-07
I have a hard drive with windows 250 gigs and a seperate drive with 30 gigs. I tried to install Kubuntu on the 30 gig drive and installed successfully but when booted back up it showed only the windows boot loader and I could not boot into Kubuntu.

So I thought maybe I forgot to install the boot loader, this time I did the partition on my main drive and installed Kubuntu. Still booted only with Windows Boot loader.

Then I tried the newest Ubuntu and checked the advanced box at the end and saw it would install a bootloader on hd0.

Still, no linux boot loader. I am new to this and hoping someone can help me out and guide me into setting up the boot loader properly.

---

### Post by philcamlin on 2009-08-07
try reinstalling grub

Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different. Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

and do you have ubuntu drive booting befire the windows one ?

---

### Post by clownz on 2009-08-07
Thanks for the quick reply. I did try find /boot/grub/stage1 and it could not be found when I tried from the terminal in the live cd. 

I had installed Windows XP 1st, so I am assuming Windows is booting first.

Can I install grub again and set everything up manually?

---

### Post by presence1960 on 2009-08-07
We need to see exactly what your setup is and your boot process. Boot from the Ubuntu Live CD and choose "try ubuntu without any changes...", when the desktop loads download to the desktop [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/")
Then open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. When pasted here highlight all text and click the # sign on the toolbar to place code tags around the text. Then we'll see exactly what you have there.

---

### Post by clownz on 2009-08-08
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
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
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
97 heads, 1 sectors/track, 3222492 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60d855e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,581,807   312,581,745   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64244000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   446,430,284   446,430,222   7 HPFS/NTFS
/dev/sdb2         446,430,285   488,392,064    41,961,780   5 Extended
/dev/sdb5         446,430,348   486,560,654    40,130,307  83 Linux
/dev/sdb6         486,560,718   488,392,064     1,831,347  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa74ba74b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    56,115,044    56,114,982  83 Linux
/dev/sdc2          56,115,045    58,621,184     2,506,140   5 Extended
/dev/sdc5          56,115,108    58,621,184     2,506,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="EAC4937DC4934B29" LABEL="XTV_STR_DSK" TYPE="ntfs" 
/dev/sdb1: UUID="00BC3665BC36557E" TYPE="ntfs" 
/dev/sdb5: UUID="6842b5eb-3894-4b07-a66b-a4652979076f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="4db0f53d-da13-43d0-a83c-2b751b8653f4" TYPE="swap" 
/dev/sdc1: UUID="6541daf4-1e0b-486b-8810-b1bdf520b87d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="17837fd3-0fe1-40e2-93e2-836d2c847494" TYPE="swap" 

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
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=6842b5eb-3894-4b07-a66b-a4652979076f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6842b5eb-3894-4b07-a66b-a4652979076f

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
uuid        6842b5eb-3894-4b07-a66b-a4652979076f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6842b5eb-3894-4b07-a66b-a4652979076f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6842b5eb-3894-4b07-a66b-a4652979076f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6842b5eb-3894-4b07-a66b-a4652979076f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6842b5eb-3894-4b07-a66b-a4652979076f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5516b681-d412-48da-9e95-0f217cadb7f4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5516b681-d412-48da-9e95-0f217cadb7f4 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 9.04, memtest86+ (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=6842b5eb-3894-4b07-a66b-a4652979076f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4db0f53d-da13-43d0-a83c-2b751b8653f4 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 237.6GB: boot/grub/menu.lst
 237.6GB: boot/grub/stage2
 237.6GB: boot/initrd.img-2.6.28-11-generic
 237.6GB: boot/vmlinuz-2.6.28-11-generic
 237.6GB: initrd.img
 237.6GB: vmlinuz

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6541daf4-1e0b-486b-8810-b1bdf520b87d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6541daf4-1e0b-486b-8810-b1bdf520b87d

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
uuid        6541daf4-1e0b-486b-8810-b1bdf520b87d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6541daf4-1e0b-486b-8810-b1bdf520b87d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6541daf4-1e0b-486b-8810-b1bdf520b87d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6541daf4-1e0b-486b-8810-b1bdf520b87d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6541daf4-1e0b-486b-8810-b1bdf520b87d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6842b5eb-3894-4b07-a66b-a4652979076f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6842b5eb-3894-4b07-a66b-a4652979076f ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=6541daf4-1e0b-486b-8810-b1bdf520b87d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=17837fd3-0fe1-40e2-93e2-836d2c847494 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  11.2GB: boot/grub/menu.lst
  11.1GB: boot/grub/stage2
  10.7GB: boot/initrd.img-2.6.28-11-generic
  10.7GB: boot/vmlinuz-2.6.28-11-generic
  10.7GB: initrd.img
  10.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd 


as you can see I tried to install kubuntu and ubuntu on different drives. Thanks for your help in advance.
```

---

### Post by presence1960 on 2009-08-08
your GRUB is installed on MBR of sda (160GB). Go into BIOS and set the 160 GB hard disk as first boot in the hard drive boot order. This will bring up GRUB when you boot. You may have to edit your windows entry to boot windows. After you make the change in BIOS note the exact boot order of your hard disks so we can get windows booting from GRUB also.

---

### Post by clownz on 2009-08-08
Thanks for your help presence,
    I went into the Bios and I tried all the HDD listed, HDD 1, HDD 2, HDD 3 and all of them seem to boot from the windows boot loader. If it's easy I dont mind going back through the ubuntu/kubuntu install and I know at option 7 I can click advanced.

    Based on the boot loader file you have seen on here from my computer, is there any easy way under the advanced settings tab on 7 to make sure it is installed onto the main boot record for my drives? or can I copy grub to my MBR and always add windows into it later?

Thanks in advance

---

### Post by presence1960 on 2009-08-08
I think we are having trouble understanding because we use terms differently. GRUB is a bootloader. It is installed onto the MBR of your 160 GB hard disk. Windows has it's own type of bootloader. GRUB must be configured from within Ubuntu or the Ubuntu Live CD through use of terminal.

When a computer boots there is a setting in BIOS which determines what devices boot and in what order. Most, not all, have the CD/DVD drive first boot. This is so when you boot from a bootable disk that disk will then do it's thing. The Ubuntu Live CD is an example of a bootable disk, as is a windows installation CD/DVD. When it gets to the hard disk whatever bootloader is in the MBR of that hard disk takes over (such as GRUB). In a mult-hard disk system you need a bootloader on MBR of your first disk.

That being said your GRUB (GRand Unified Bootloader) is on MBR of your 160 GB disk which is sda. You need to find out which of those hard disk designations in BIOS is 160 GB (sda) hard disk and set that to the first hard disk spot in the hard disk boot order. Then when you boot your machine GRUB will take over. It has nothing to do with windows, your BIOS controls getting your machine and it's devices running properly.

Forget about windows for a moment and find out whether hard disk 1, hard disk 2, or hard disk 3 represents your 160 GB hard drive. Set that to first boot in the hard disk boot order. Then boot your machine and watch GRUB. GRUB is installed, it is there, it just needs the hard disk it is on to be booted before the other hard disks. The other hard disks have windows bootloader on their MBRs - that is why it is going right to windows when you boot. You have one of the other two hard disks set to boot first. Your machine will only do what  you tell it to do. That's where BIOS comes in. Set BIOS correctly and GRUB will boot.

---

### Post by presence1960 on 2009-08-08
If the above does not work go back in BIOS and let me know which hard disk boots first, second, then third. We will then try to restore GRUB to the first boot disk. Simple matter so don't sweat it. Report back when you can, I will be on & off a lot today

---

