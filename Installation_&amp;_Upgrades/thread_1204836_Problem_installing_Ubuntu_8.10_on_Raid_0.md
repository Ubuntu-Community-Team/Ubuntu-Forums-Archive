---
title: "Problem installing Ubuntu 8.10 on Raid 0"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by gemini6 on 2009-07-05
First of all I am a newbie. Hope you understand.
I tried installing 9.04 on an onboard Raid 0 and want to dual-boot with windows. It comprises 2 HD, and 2 partitions were created on the raid level, 1 50G (25+25) and the other 1.15T (575+575). There is Windows7 installed on the 50G partition.

First I followed this how-to to install [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
, using live cd, and got the exact same problem described in this thread [http://ubuntuforums.org/showthread.php?t=1198990&highlight=raid](http://ubuntuforums.org/showthread.php?t=1198990&highlight=raid)

Then I tried using 8.10. This time everything went smooth. I made room in the 50G partition for the linux partitions, by shrinking the windows7 partition using gparted.

However after reboot and select Ubuntu, nothing showed up but just a blank screen with a blinking cursor. Windows7 also failed to boot.

I thought the partitioning process went wrong. So I decided to wipe the windows partition as well, letting the guided installation to choose the entire 50G disk. Everything went ok as well. But after reboot, same issue.

Can someone shield some light on this? Thanks a lot.

---

### Post by ronparent on 2009-07-05
You will have to investigate booting from the live cd. What does menu.lst read? It sounds likely that one of the two boot files called by the menu.lst boot instructions is not being found. what is the output of **ls /boot**?

---

### Post by gemini6 on 2009-07-05
May I know how to view the files in the Ubuntu partitions using Live cd?
I tried mounting it but it says target does not exist.
```

ubuntu@ubuntu:/dev/mapper$ sudo mount pdc_cdcaicggge5 /target/
mount: mount point /target/ does not exist

```

---

### Post by QIII on 2009-07-05
Advanced options like RAID are installed using the "Alternate" disk.

---

### Post by ronparent on 2009-07-05
You have to manually create /target. It must exist in the file system of the live cd session prior to mounting to it. Remember in operating from the live cd /target does not exist until you create it. Also, unless you have already installed dmraid to the live cd session, you will not find /dev/mapper/pdc_cdcaicggge5 either! My  bad if you were  not already aware of it. 

To install and activate dmraid with the 8.10 live cd, in a terminal enter **sudo apt-get install dmraid -y**, Once you find the the symbolic link pdc_cdcaicggge5 in /dev/mapper you will be able to mount it. Yell if you need more help.

---

### Post by gemini6 on 2009-07-06
Thanks for your reply ronparent. I am aware that I should install dmraid before I can find /dev/mapper/pdc_cdcaicggge5 by following the FakeRaidHowto. But it just does not mention about creating the /target mount point.
Here is the content of menu.lst and that in the /boot directory. Am I missing something?

```

root@ubuntu:/boot/grub# more menu.lst
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
timeout        5

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
# kopt=root=/dev/mapper/pdc_cdcaicggge5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/pdc_cdcaicggge5 
ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/pdc_cdcaicggge5 
ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin

title        Windows 7
rootnoverify    (hd0,0)
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST
root@ubuntu:/boot/grub#  
root@ubuntu:/boot/grub# 
root@ubuntu:/boot/grub# ls -al /boot
total 12104
drwxr-xr-x  3 root root    4096 2009-07-06 03:34 .
drwxr-xr-x 20 root root    4096 2009-07-06 03:21 ..
-rw-r--r--  1 root root  507665 2008-10-24 16:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 16:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-07-06 03:38 grub
-rw-r--r--  1 root root 8339408 2009-07-06 03:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-12 04:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 16:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 16:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 16:29 vmlinuz-2.6.27-7-generic
root@ubuntu:/boot/grub# 
root@ubuntu:/boot/grub# ls -al /boot/grub
total 340
drwxr-xr-x 2 root root   4096 2009-07-06 03:38 .
drwxr-xr-x 3 root root   4096 2009-07-06 03:34 ..
-rw-r--r-- 1 root root    191 2009-07-06 03:36 default
-rw-r--r-- 1 root root   8108 2009-07-06 03:34 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-07-06 03:34 fat_stage1_5
-rw-r--r-- 1 root root   8712 2009-07-06 03:34 jfs_stage1_5
-rw-r--r-- 1 root root   4206 2009-07-06 03:38 menu.lst
-rw-r--r-- 1 root root   4206 2009-07-06 03:38 menu.lst~
-rw-r--r-- 1 root root   7352 2009-07-06 03:34 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-07-06 03:34 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-07-06 03:34 stage1
-rw-r--r-- 1 root root 121460 2009-07-06 03:34 stage2
-rw-r--r-- 1 root root 121460 2009-07-06 03:34 stage2_eltorito
-rw-r--r-- 1 root root   9556 2009-07-06 03:34 xfs_stage1_5
root@ubuntu:/boot/grub# 


```

---

### Post by gemini6 on 2009-07-06
> **QIII said:**
> Advanced options like RAID are installed using the "Alternate" disk.
I did tried this but to no avail.

---

### Post by ronparent on 2009-07-06
I would be more comfortable if root were specified by root=UUID= <etc>. I know that works. It is possible that the symbolic links are not created in the boot process until the kernel is loaded. If that is the case the reference to the drive by a /dev/mapper symbolic link would not find the kernel? The finding of the root drive by UUID is the most current default when grub automatically creates the entries in menu.lst during install.

---

### Post by gemini6 on 2009-07-07
May I know how I can find this UUID out? Thanks a lot.

---

### Post by gemini6 on 2009-07-07
I did a google and found it. Will try it out tonight.

---

### Post by gemini6 on 2009-07-07
I tried using UUID, but still same result.

```

root@ubuntu:/# cat /boot/grub/menu.lst
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
default        3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        7

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
# kopt=root=/dev/mapper/pdc_cdcaicggge5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
#root        (hd0,4)
uuid        b40b7176-e04b-426d-89cf-dd3cac25d816
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b40b7176-e04b-426d-89cf-dd3cac25d816 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#root        (hd0,4)
uuid        b40b7176-e04b-426d-89cf-dd3cac25d816
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b40b7176-e04b-426d-89cf-dd3cac25d816 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
#root        (hd0,4)
uuid        b40b7176-e04b-426d-89cf-dd3cac25d816
kernel        /boot/memtest86+.bin

title        Windows 7
rootnoverify    (hd0,0)
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST
root@ubuntu:/# 
root@ubuntu:/# blkid
/dev/sdc1: UUID="9ABE2D58BE2D2E67" LABEL="Collection" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/mapper/pdc_cdcaicggge1: UUID="A6D08E68D08E3E95" LABEL="Windows7" TYPE="ntfs" 
/dev/mapper/pdc_cdcaicggge5: UUID="b40b7176-e04b-426d-89cf-dd3cac25d816" TYPE="ext3" 
/dev/mapper/pdc_cdcaicggge6: UUID="ee3dd0fa-dc3d-4a12-8382-da78915a4b82" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/pdc_cdcaicggge7: TYPE="swap" UUID="f2f923cc-4efd-4650-b075-9083e728c94a" 
root@ubuntu:/# 


```

Any more hint? Thanks a lot.

---

### Post by gemini6 on 2009-07-07
I managed to boot ubuntu accidentally in a weird way.
I first boot off the 8.10 live cd. From the menu, I choose "boot from the first harddisk". Then ubuntu boots! So what exactly does this option do? I just don't want to boot everytime like this. Thanks a lot.

---

