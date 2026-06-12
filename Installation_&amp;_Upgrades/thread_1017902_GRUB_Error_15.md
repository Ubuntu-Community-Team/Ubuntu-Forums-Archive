---
title: "GRUB Error 15"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Evil Ninja on 2008-12-21
So, I just finished some updating with Ubuntu and had to restart my system. When I restarted it got to a certain point and then I got this error. The screen looks like this right now...

```
GRUB Loading stage1.5

GRUB loading, please wait...
Error 15
```


I'm clueless.

---

### Post by Sealbhach on 2008-12-21
Hi, boot up from the Live CD and follow these instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


.

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by Evil Ninja on 2008-12-21
> **Sealbhach said:**
> Hi, boot up from the Live CD and follow these instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


.

After both find attempts, it could not find it on either try.

> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

Here are the results...

```
Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #1 for its boot files.
Windows is installed in the MBR of /dev/sdb

sda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /etc/fstab /boot

sda2:
    File system:  Extended Partition

sda5:
    File system:  swap

sdb1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45ff45fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300865319   150432628+  83  Linux
/dev/sda2       300865320   312576704     5855692+   5  Extended
/dev/sda5       300865383   312576704     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce8d5882

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux


/dev/sda1: UUID="a1619353-edf1-4902-9b5a-01e4ad54925e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b14ee239-4488-4d59-95c9-9660337f26dd" 
/dev/sdb1: UUID="9567a5e8-5510-49fa-b76a-4deb6d58f1ae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a1619353-edf1-4902-9b5a-01e4ad54925e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=55cb273c-f26a-47e3-bc99-75de0e7a260a /boot           ext3    relatime        0       2
# /dev/sda5
UUID=b14ee239-4488-4d59-95c9-9660337f26dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/mynewdrive   ext3    defaults     0        2

sda1/boot

total 25392
drwxr-xr-x  2 root root    4096 2008-12-21 20:07 .
drwxr-xr-x 21 root root    4096 2008-12-21 20:07 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
-rw-r--r--  1 root root 8670855 2008-12-21 20:06 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8670714 2008-12-21 20:07 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

StdErr Messages 

/dev/sda: OK
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK
```

Hope it helps.

--

I posted before I went to work, which is why I took so much time getting back. >_<

---

### Post by caljohnsmith on 2008-12-22
So it looks like your sda1 Ubuntu install currently doesn't have Grub installed; when you installed Ubuntu, did you click the "advanced" button near the end and have the installer omit installing Grub? 

How about from your Live CD, do:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit

```
And please post the output of all the above commands. You will need an internet connection from the Live CD in order to install the Grub package as given by the apt-get command above, so let me know if you don't have an internet connection when using the Live CD. Next reboot, and let me know exactly what happens on start up. We can go from there.

---

### Post by Evil Ninja on 2008-12-22
> **caljohnsmith said:**
> So it looks like your sda1 Ubuntu install currently doesn't have Grub installed; when you installed Ubuntu, did you click the "advanced" button near the end and have the installer omit installing Grub? 

How about from your Live CD, do:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit

```
And please post the output of all the above commands. You will need an internet connection from the Live CD in order to install the Grub package as given by the apt-get command above, so let me know if you don't have an internet connection when using the Live CD. Next reboot, and let me know exactly what happens on start up. We can go from there.

Nope. Actually, Ubuntu was fine until I restarted it to apply some updates.



After "sudo chroot /mnt" I got this...

```
chroot: cannot run command '/bin/bash': Exec format error
```

After "apt-get install grub" it had some error about being an admin and asked if I was root. I just typed "yes" and it flipped, spamming a ton of y's. I can't type in the terminal anymore.

---

### Post by caljohnsmith on 2008-12-22
Please copy/paste your terminal session, so I can see the output of all the following commands:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
mount
ls -l /mnt/bin/bash
sudo chroot /mnt

```

---

### Post by Evil Ninja on 2008-12-22
> **caljohnsmith said:**
> Please copy/paste your terminal session, so I can see the output of all the following commands:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
mount
ls -l /mnt/bin/bash
sudo chroot /mnt

```

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt type ext3 (rw)
/dev on /mnt/dev type none (rw,bind)
/proc on /mnt/proc type none (rw,bind)
/dev on /mnt/dev type none (rw,bind)
/proc on /mnt/proc type none (rw,bind)
ubuntu@ubuntu:~$ ls -1 /mnt/bin/bash
/mnt/bin/bash
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error

```

---

### Post by caljohnsmith on 2008-12-22
What is the architecture of your Ubuntu install, and what is it for the Live CD you are using (i.e. 32-bit vs. 64-bit)? Also, since you were previously able to use Ubuntu OK, do you have any idea what would have deleted your /boot/grub directory? Did you happen to do anything or was it the updates? Also, what is in the sdb1 partition?

---

### Post by Evil Ninja on 2008-12-22
> **caljohnsmith said:**
> What is the architecture of your Ubuntu install, and what is it for the Live CD you are using (i.e. 32-bit vs. 64-bit)? Also, since you were previously able to use Ubuntu OK, do you have any idea what would have deleted your /boot/grub directory? Did you happen to do anything or was it the updates? Also, what is in the sdb1 partition?

The install is 64-bit, the Live CD is 32-bit. The install is also 8.10, the Live CD is 8.04. Both 8.10 CD's that I have (32 and 64-bit) won't boot. They hang at some point and I don't remember what it said. I don't know what could have deleted the grub directory. The only thing I did before updating and restarting Ubuntu was getting my second hard drive partitioned correctly ([thread]("http://ubuntuforums.org/showthread.php?t=1017563")). A few of the updates failed, but I didn't imagine they would delete the grub install. The sdb1 partition is my second, blank hard drive, I think.

---

### Post by caljohnsmith on 2008-12-22
> **Evil Ninja said:**
> The install is 64-bit, the Live CD is 32-bit.
OK, that explains the problem. :) It's OK to use a previous version of the Ubuntu Live CD, but it must be the same architecture as your installed Ubuntu in order to use that chroot command. Can you download a 64-bit Ubuntu version? Or do you have any other 64-bit Live CD's of other distros you can use? We could recreate the menu.lst manually, but that would be more trouble than it is worth if you can get your hands on a 64-bit Live CD.

---

### Post by meierfra. on 2008-12-22
caljohnsmith: did you noticed that according to "fstab" sdb1 is mounted to /boot.

---

### Post by caljohnsmith on 2008-12-22
> **meierfra. said:**
> caljohnsmith: did you noticed that according to "fstab" sdb1 is mounted to /boot.
No, I missed that, thanks for pointing that out. :) Evil Ninja, it looks like that is part of the problem, because according to the script output your sdb1 partition does not have a grub directory. Also, your fstab has the wrong UUID for the sdb1 partition. Did you reformat the sdb1 partition without realizing that it was your /boot partition? It looks like that might be the issue. How about posting the output of:
```
sudo mkdir /tmp/sdb1
sudo mount /dev/sdb1 /tmp/sdb1
ls -l /tmp/sdb1
```
And we can work from there.

---

### Post by Evil Ninja on 2008-12-22
> **caljohnsmith said:**
> No, I missed that, thanks for pointing that out. :) Evil Ninja, it looks like that is part of the problem, because according to the script output your sdb1 partition does not have a grub directory. Also, your fstab has the wrong UUID for the sdb1 partition. Did you reformat the sdb1 partition without realizing that it was your /boot partition? It looks like that might be the issue. How about posting the output of:
```
sudo mkdir /tmp/sdb1
sudo mount /dev/sdb1 /tmp/sdb1
ls -l /tmp/sdb1
```
And we can work from there.

```
ubuntu@ubuntu:~$ sudo mkdir /tmp/sdb1
ubuntu@ubuntu:~$ sudo mount dev/sdb1 /tmp/sdb1
mount: special device dev/sdb1 does not exist
ubuntu@ubuntu:~$ ls -l /tmp/sdb1
total 0
```


And thinking about it, I did reformat it.

---

### Post by caljohnsmith on 2008-12-23
> **Evil Ninja said:**
> 
And thinking about it, I did reformat it.
If that's the case, it would be best if you can get a 64-bit Live CD so we can follow through with the previous chroot commands in order to install Grub to your sda1 partition. At least you still have Ubuntu's boot files in sda1, so you won't have to install those too. Let me know how it goes.

---

### Post by Evil Ninja on 2008-12-23
> **caljohnsmith said:**
> If that's the case, it would be best if you can get a 64-bit Live CD so we can follow through with the previous chroot commands in order to install Grub to your sda1 partition. At least you still have Ubuntu's boot files in sda1, so you won't have to install those too. Let me know how it goes.

Ok, this is what I got this time...

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt type ext3 (rw)
/dev on /mnt/dev type none (rw,bind)
/proc on /mnt/proc type none (rw,bind)
ubuntu@ubuntu:~$ ls -l /mnt/bin/bash
-rwxr-xr-x 1 root root 830424 2008-05-12 18:49 /mnt/bin/bash
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```

EDIT: Unless you wanted me to do the commands to reinstall grub?

DOUBLE: This is on 64-bit Live CD now too.

---

### Post by caljohnsmith on 2008-12-23
Yes, after doing the chroot command, continue with:
```
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit
```
And please post the output of all the above commands.

---

### Post by Evil Ninja on 2008-12-23
> **caljohnsmith said:**
> Yes, after doing the chroot command, continue with:
```
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit
```
And please post the output of all the above commands.

```
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-7.14 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-7.14 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=55cb273c-f26a-47e3-bc99-75de0e7a260a'
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=55cb273c-f26a-47e3-bc99-75de0e7a260a'
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-restricted-modules-2.6.27-9-generic (2.6.27-9.13) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic

Setting up linux-image-generic (2.6.27.9.13) ...
Setting up linux-restricted-modules-generic (2.6.27.9.13) ...
Setting up linux-generic (2.6.27.9.13) ...
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=55cb273c-f26a-47e3-bc99-75de0e7a260a'
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Updating /boot/grub/menu.lst ... done

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
default		0

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
# kopt=root=UUID=a1619353-edf1-4902-9b5a-01e4ad54925e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a1619353-edf1-4902-9b5a-01e4ad54925e

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a1619353-edf1-4902-9b5a-01e4ad54925e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a1619353-edf1-4902-9b5a-01e4ad54925e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a1619353-edf1-4902-9b5a-01e4ad54925e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a1619353-edf1-4902-9b5a-01e4ad54925e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a1619353-edf1-4902-9b5a-01e4ad54925e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a1619353-edf1-4902-9b5a-01e4ad54925e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a1619353-edf1-4902-9b5a-01e4ad54925e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a1619353-edf1-4902-9b5a-01e4ad54925e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2008-12-23
Great, looks like you might be set. How about rebooting, make sure you have your BIOS set to boot the sda drive, and then you'll have to press the ESC key to see the Grub menu when you boot the drive. It looks like you should be able to boot into Ubuntu just fine from the Grub menu. Let me know how it goes.

---

### Post by Evil Ninja on 2008-12-23
> **caljohnsmith said:**
> Great, looks like you might be set. How about rebooting, make sure you have your BIOS set to boot the sda drive, and then you'll have to press the ESC key to see the Grub menu when you boot the drive. It looks like you should be able to boot into Ubuntu just fine from the Grub menu. Let me know how it goes.

Victory! It works fine now! Thanks a lot for the help. :) I really appreciate it.

---

### Post by caljohnsmith on 2008-12-23
That's great news, glad to hear it worked OK. Cheers and happy holidays. :)

---

### Post by caljohnsmith on 2008-12-23
Evil Ninja, meierfra reminded me of one last detail I think you will want to take care of; it would be good to modify your fstab so that you aren't still mounting your sdb1 partition on /boot. How about doing the following:
```
gksudo gedit /etc/fstab
```
And simply delete the following lines:
```
# /dev/sdb1
UUID=55cb273c-f26a-47e3-bc99-75de0e7a260a /boot   ext3   relatime  0  2
```
That should hopefully be everything now. :)

---

### Post by Evil Ninja on 2008-12-23
> **caljohnsmith said:**
> Evil Ninja, meierfra reminded me of one last detail I think you will want to take care of; it would be good to modify your fstab so that you aren't still mounting your sdb1 partition on /boot. How about doing the following:
```
gksudo gedit /etc/fstab
```
And simply delete the following lines:
```
# /dev/sdb1
UUID=55cb273c-f26a-47e3-bc99-75de0e7a260a /boot   ext3   relatime  0  2
```
That should hopefully be everything now. :)

Done and done. Thanks. :)

---

