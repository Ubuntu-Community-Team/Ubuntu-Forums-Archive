---
title: "[SOLVED] GRUB and booting error"
date: 2008-08-29
forum: General Help
---

### Post by Zylaxice on 2008-08-29
Let me preface this by saying that I'm pretty new to Ubuntu, and Linux in general, but am willing to follow any steps that might lead to a solution, and I apologize in advance if I'm a bit dense in my responses, any help is appreciated.

I've been using GRUB, as I have both Xubuntu Hardy Heron and Windows XP on my machine.  This morning, I tried to boot into Xubuntu and was faced with an error
> kernel panic-not syncing VFS:unable to mount root fs on an unknown-block(0,0)

The same error occurs when I try to boot into the "(recovery mode)" version of the kernel. I can get into Windows just fine.  

I did a bit of research on the error, but most of the solutions are far beyond my limited comprehension, and seem quite dire. If anyone has any suggestions about how to further test the problem and hopefully restore my system, I'd be thrilled.

---

### Post by Elfy on 2008-08-29
Can you boot an older kernel - go down to the next menu option and try that to get in.

---

### Post by Zylaxice on 2008-08-29
Stupidly, I only had the one kernel installed.

---

### Post by caljohnsmith on 2008-08-29
Try booting a Live CD, open a terminal, and do:
```
sudo fdisk -l
```
Figure out which is your Ubuntu partition in the form /dev/sdaX, and then mount it:
```
sudo mount /dev/sdaX /mnt
sudo chroot /mnt
sudo apt-get install linux-image-2.6.24.16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
```
Replace the above kernel numbers with whichever new kernel you want to install, and hopefully a different kernel will solve your problems. Let me know if you need more details.

---

### Post by Zylaxice on 2008-08-29
> **caljohnsmith said:**
> Try booting a Live CD, open a terminal, and do:
```
sudo fdisk -l
```
Figure out which is your Ubuntu partition in the form /dev/sdaX, and then mount it:
```
sudo mount /dev/sdaX /mnt
sudo chroot /mnt
sudo apt-get install linux-image-2.6.24.16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
```
Replace the above kernel numbers with whichever new kernel you want to install, and hopefully a different kernel will solve your problems. Let me know if you need more details.


Thanks for the suggestion. When I try the last step, I get the error
```
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.24.16-generic
```

I get this with most other kernels, except for .19, which it says is already installed and updated, and .18, which returns a string of "Could not resolve 'security.ubuntu.com' "


I'm connected to the internet, and my /etc/hosts reads

```
127.0.0.1 localhost
127.0.1.1 david-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by caljohnsmith on 2008-08-29
Which computer is "david-laptop"? Is that the same computer as the one you can't boot into Xubuntu? Or is that from the Live CD? I assume you still can't boot at all into Xubuntu, is that true? 

You could download those kernel packages I gave in my previous post from [http://packages.ubuntu.com](http://packages.ubuntu.com), and then manually install the deb packages. If you are doing that from the Live CD, you would have to mount your Xubuntu partition and "chroot" into it first, like before. Once you've chrooted into the mounted partition, just go to the directory where you downloaded the .deb files and run:
```
dpkg -i *.deb
```
(I don't think you have to run dpkg with sudo since you chrooted into the partition, but add sudo if the command complains). Let me know if you need more info/details.

---

### Post by Zylaxice on 2008-08-29
> **caljohnsmith said:**
> Which computer is "david-laptop"? Is that the same computer as the one you can't boot into Xubuntu? Or is that from the Live CD? I assume you still can't boot at all into Xubuntu, is that true? 

david-laptop is the computer that I can't boot into Xubuntu on.  But I retrieved that table by opening the /etc/hosts on the LiveCD (after having mounted my Ubuntu partition as you described)

> **caljohnsmith said:**
> 
You could download those kernel packages I gave in my previous post from [http://packages.ubuntu.com](http://packages.ubuntu.com), and then manually install the deb packages. If you are doing that from the Live CD, you would have to mount your Xubuntu partition and "chroot" into it first, like before. Once you've chrooted into the mounted partition, just go to the directory where you downloaded the .deb files and run:
```
dpkg -i *.deb
```
(I don't think you have to run dpkg with sudo since you chrooted into the partition, but add sudo if the command complains). Let me know if you need more info/details.

Thank you, I'll try that now.

---

### Post by Zylaxice on 2008-08-29
Where should I be saving these packages to? I can't seem to put them on the partition I'm chrooting to ("Permission Denied"), but I don't know how to get to them in the terminal while chrooting if I save them on the LiveCD "Desktop".

---

### Post by caljohnsmith on 2008-08-29
> **Zylaxice said:**
> Where should I be saving these packages to? I can't seem to put them on the partition I'm chrooting to ("Permission Denied"), but I don't know how to get to them in the terminal while chrooting if I save them on the LiveCD "Desktop".
You could download them to your Ubuntu Live CD desktop, and then do the following to move them to your partition (note you should have your Xubuntu partition mounted like before, but should not be in the chroot environment yet):
```
cd ~/Desktop
sudo mv *.deb /mnt/home/<username>/Desktop/.
```
Replace <username> with your Xubuntu username. After you've moved them, then you can do the "chroot" command as before, and then install the packages with "dpkg":
```
sudo chroot /mnt
cd /home/<username>/Desktop
dpkg -i *.deb
```

---

### Post by Zylaxice on 2008-08-29
Thanks for your patience. The installation generated the following output.

```
root@ubuntu:/home/david/Desktop# dpkg -i *.deb
Selecting previously deselected package linux-image-2.6.24-16-generic.
(Reading database ... 95845 files and directories currently installed.)
Unpacking linux-image-2.6.24-16-generic (from linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb) ...
Done.
Selecting previously deselected package linux-restricted-modules-2.6.24-16-generic.
Unpacking linux-restricted-modules-2.6.24-16-generic (from linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb) ...
Selecting previously deselected package linux-ubuntu-modules-2.6.24-16-generic.
Unpacking linux-ubuntu-modules-2.6.24-16-generic (from linux-ubuntu-modules-2.6.24-16-generic_2.6.24-16.23_i386.deb) ...
Setting up linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
findfs: Unable to resolve 'UUID=5c4c607f-3e09-4ec8-95b1-51f4e87bd5f3'
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Updating /boot/grub/menu.lst ... done


Setting up linux-restricted-modules-2.6.24-16-generic (2.6.24.12-16.34) ...

Setting up linux-ubuntu-modules-2.6.24-16-generic (2.6.24-16.23) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
```

However, at boot-up I still only see the same GRUB options as before, the .19 kernel (which gives a kernel panic error) and my windows install.

---

### Post by caljohnsmith on 2008-08-29
When installing that kernel, it said it couldn't find your Grub's /boot/grub/menu.lst. Do you have Grub on any other partition? Please post the output of all the following (assuming your Xubuntu partition is mounted on /mnt like before, but you are not chrooted):
```
cat /etc/fstab
sudo blkid -c /dev/null
sudo fdisk -lu
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst
sudo grub
  grub> find /boot/grub/stage1
  grub> quit
```

---

### Post by Elfy on 2008-08-29
I can't see a menu list not found - but there could be a UUID problem.

> Unable to resolve 'UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32'
Cannot determine root device.  Assuming /dev/hda1

---

### Post by Zylaxice on 2008-08-29
```
**ubuntu@ubuntu:~$ cat /etc/fstab**
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0
**ubuntu@ubuntu:~$ sudo blkid -c /dev/null**
/dev/sda1: UUID="1AF847E1F847BA31" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="257fc41f-f924-4fe4-a834-212cb9f2bd9d" 
/dev/sda3: UUID="5c4c607f-3e09-4ec8-95b1-51f4e87bd5f3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="335f8503-50e2-43b9-b986-4f1eda1eaa32" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
```
```
**ubuntu@ubuntu:~$ sudo fdisk -lu**

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders, total 231496650 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31744439    15872188+   7  HPFS/NTFS
/dev/sda2        31744440    35744624     2000092+  82  Linux swap / Solaris
/dev/sda3        35744625    35841014       48195   83  Linux
/dev/sda4        35841015   231496649    97827817+  83  Linux


```
```
**ubuntu@ubuntu:~$ ls -lR /mnt/boot**
/mnt/boot:
total 21180
-rw-r--r-- 1 root root  422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-08-21 04:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   79964 2008-04-10 16:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80049 2008-08-21 04:46 config-2.6.24-19-generic
drwxr-xr-x 2 root root    4096 2008-08-29 20:59 grub
-rw-r--r-- 1 root root 7485130 2008-08-29 20:08 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7485361 2008-08-29 19:59 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root  899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905170 2008-08-21 04:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 04:46 vmlinuz-2.6.24-19-generic

/mnt/boot/grub:
total 24
-rw-r--r-- 1 root root  191 2008-08-29 20:07 default
-rw-r--r-- 1 root root   15 2008-08-29 20:01 device.map
-rw-r--r-- 1 root root 4451 2008-08-29 20:59 menu.lst
-rw-r--r-- 1 root root 4451 2008-08-29 20:58 menu.lst~
```

```
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic


### END DEBIAN AUTOMAGIC KERNELS LIST
```

sudo grub
  grub> find /boot/grub/stage1
```
Error 15: File Not Found
```
  grub> quit

---

### Post by caljohnsmith on 2008-08-29
OK, I think I know what is going on; I'll bet your Grub files are on that other linux partition you have, sda3. Did you at some point set up a dedicated Grub partition and/or /boot partition? It looks like that might be what's going on here. Please post the following after you have your Xubuntu mounted on /mnt again:
```
cat /mnt/etc/fstab
sudo grub
grub> find /grub/stage1
grub> quit
```

---

### Post by Zylaxice on 2008-08-29
I think I have a small /boot partition (the 50 meg one), but was mostly guided through an install process by a friend, so I don't know exactly how it was done.

```
grub> find /grub/stage1
 (hd0,2)

```

That output is consistent with the GRUB files being on sda3, my /boot partition, if I'm understanding right.

---

### Post by caljohnsmith on 2008-08-29
OK, that confirms my suspicions. Please do the following:
```
sudo umount -a  [COLOR="Blue"][just to make sure nothing is mounted, don't worry about an error][/COLOR]
sudo mkdir /mnt/sda3
sudo mkdir /mnt/sda4
sudo mount /dev/sda3 /mnt/sda3
sudo mount /dev/sda4 /mnt/sda4
cat /mnt/sda4/etc/fstab
ls -lR /mnt/sda3
cat /mnt/sda3/grub/menu.lst
```

---

### Post by Zylaxice on 2008-08-29
```
ubuntu@ubuntu:~$ sudo umount -a
umount: /tmp: device is busy
umount: /dev/shm: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: tmpfs: not found
umount: /lib/modules/2.6.24-19-generic/volatile: not mounted
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda3
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda4
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/sda3
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt/sda4

```

```
ubuntu@ubuntu:~$ cat /mnt/sda4/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=5c4c607f-3e09-4ec8-95b1-51f4e87bd5f3 /boot           ext3    relatime        0       2
# /dev/sda2
UUID=257fc41f-f924-4fe4-a834-212cb9f2bd9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
ubuntu@ubuntu:~$ ls -lR /mnt/sda3
/mnt/sda3:
total 3373
-rw-r--r-- 1 root root  422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x 2 root root    1024 2008-08-28 21:46 grub
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

/mnt/sda3/grub:
total 169
-rw-r--r-- 1 root root    197 2008-08-28 21:46 default
-rw-r--r-- 1 root root     30 2008-08-28 21:46 device.map
-rw-r--r-- 1 root root   8056 2008-08-28 21:46 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-08-28 21:46 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-08-28 21:46 installed-version
-rw-r--r-- 1 root root   8608 2008-08-28 21:46 jfs_stage1_5
-rw-r--r-- 1 root root   4481 2008-08-28 21:46 menu.lst
-rw-r--r-- 1 root root   7324 2008-08-28 21:46 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-08-28 21:46 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-08-28 21:46 stage1
-rw-r--r-- 1 root root 108356 2008-08-28 21:46 stage2
-rw-r--r-- 1 root root   9276 2008-08-28 21:46 xfs_stage1_5

```

```
ubuntu@ubuntu:~$ cat /mnt/sda3/grub/menu.lst
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
# kopt=root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro quiet splash
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro single

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

That menu.lst matches what I'm seeing on bootup.
I feel like I should know how to fix this from here, but I'm still lost on how to get things operational again.

---

### Post by caljohnsmith on 2008-08-29
Sorry, double post, see the next one.

---

### Post by caljohnsmith on 2008-08-29
OK, with everything still mounted, please do the following:
```
gksudo gedit /mnt/sda3/grub/menu.lst &
```
For your Ubuntu entries:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/vmlinuz-2.6.24-19-generic root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro quiet splash
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/vmlinuz-2.6.24-19-generic root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro single

title		Ubuntu 8.04.1, memtest86+
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/memtest86+.bin
quiet
```
For the above entries, change (hd0,2) to (hd0,3). Also do the following:
```
sudo rm /mnt/sda4/boot/grub/menu.lst
sudo ln -s /mnt/sda3/grub/menu.lst /mnt/sda4/boot/grub/.

```
Reboot, and I think Xubuntu should boot just fine.

---

### Post by Zylaxice on 2008-08-29
Argh, new errors again.  When I try to boot now, I get "Error 15: File Not Found".

---

### Post by caljohnsmith on 2008-08-29
OK, I missed part of the problem with your Ubuntu entries in menu.lst. Open that menu.lst again, and change your Ubuntu entries to look like:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		[COLOR="Blue"]/boot[/COLOR]/vmlinuz-2.6.24-19-generic root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro quiet splash
[COLOR="Blue"]initrd		/boot/initrd.img-2.6.24-19-generic[/COLOR]
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		[COLOR="Blue"]/boot[/COLOR]/vmlinuz-2.6.24-19-generic root=UUID=335f8503-50e2-43b9-b986-4f1eda1eaa32 ro single
[COLOR="Blue"]initrd		/boot/initrd.img-2.6.24-19-generic[/COLOR]


title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
```
In other words, your Ubuntu entries were missing the "initrd" lines. Reboot and see if that fixes everything. :)

EDIT: caught another error.

---

### Post by Zylaxice on 2008-08-29
Unfortunately, that doesn't seem to have changed much of anything. Still getting Error 15 whenever I try to boot the kernel.

---

### Post by caljohnsmith on 2008-08-29
OK, I think I found the error. I corrected my previous post above, Zylaxice; you need to add /boot/ before those vmlinuz lines. Sorry I didn't catch that sooner.

---

### Post by falcon61102 on 2008-08-29
I was just reading over everything and I might have noticed an error.

In post #19 you have the menu.lst being changed to (hd0,2) then in post #21 its back to (hd0,3), was that intentional?

And based on his previous fdisk -l and fstab entries, I think the original (hd0,2) was correct.

---

### Post by caljohnsmith on 2008-08-29
> **falcon61102 said:**
> I was just reading over everything and I might have noticed an error.

In post #19 you have the menu.lst being changed to (hd0,2) then in post #21 its back to (hd0,3), was that intentional?
Actually, maybe my post #19 was a little confusing, because if you read below where I highlighted (hd0,2), I asked Zylaxice to change (hd0,2) to (hd0,3), not the other way around. I asked him to use (hd0,3) or sda4 because that is his root Linux partition, while (hd0,2) or sda3 is just a super small partition dedicated to Grub.

Thanks for checking though, I sincerely appreciate it when someone points out any errors I may make. Let me know if you see anything else. :)

---

### Post by falcon61102 on 2008-08-29
Oops, I guess I was reading too fast.

Also, wouldn't it make more sense if his install is on /dev/sda3 for it to be (hd0,2)?

---

### Post by caljohnsmith on 2008-08-29
> **falcon61102 said:**
> Oops, I guess I was reading too fast.

Also, wouldn't it make more sense if his install is on /dev/sda3 for it to be (hd0,2)?
If his main Ubuntu install were on sda3, yes, it would be (hd0,2); but if you check his post #13, you'll see that sda3 is only a 50 MB partition, which is his dedicated Grub partition. His main Ubuntu install is sda4, which is 100 GB, so it would be (hd0,3) in Grub's Convoluted World.

---

### Post by Zylaxice on 2008-08-31
Hooray! That seems to have worked!  Thanks to everyone who voiced advice, especially caljohnsmith.

---

