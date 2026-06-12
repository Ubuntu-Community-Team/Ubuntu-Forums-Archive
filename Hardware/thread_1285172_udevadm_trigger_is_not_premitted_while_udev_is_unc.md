---
title: "udevadm trigger is not premitted while udev is unconfigured."
date: 2009-10-07
forum: Hardware
---

### Post by Andrux101 on 2009-10-07
Hello!
I'll try shortly describe my problem. In the google has many solves, but it dont helps me.
One day I install updates and was that situation my laptop restarts and after it shows that error:
[B][FONT=Arial][I]udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/05d79451-0ad0-43fc-9f51-a2c98b4831f2 does not exist.
Dropping to a shell![/I][/FONT][/B]

I'm traying that solve:
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654/comments/0](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654/comments/0)

Step by step:
The solution is to use a live-CD to mount the system (or boot from a completely separate installation), mount the failed OS partition(s), and complete the update process:


 ***e.g.***
 ***sudo -i***
 [B][I]# create a target mount point
mkdir /mnt/target[/I][/B]
 [B][I]# mount root
mount /dev/sda8 /mnt/target
# mount boot
mount /dev/sda9 /mnt/target/boot[/I][/B]
 [B][I]# into Jaunty
chroot /mnt/target/[/I][/B]
 [B][I]# update
dpkg --configure -a[/I][/B]
 [B][I]# done
exit[/I][/B]
 [B][I]#unmount
umount /mnt/target/boot
umount /mnt/target[/I][/B]


But this commands didn't follows me. What I'm doing wrong? If anyone can write what to do step by step?
Thanks!

---

### Post by MegaJim on 2009-10-07
Possibly treating the symptom rather than the problem, but is that disk uuid stale (e.g. after removing an old hard disk), perhaps it would be a good idea to confirm whether this disk exists on your system and if not, remove it from fstab...

After quick search I think that the problem is definitely the UUID, try to replace the UUID in your menu.lst with the partition path instead i.e. /dev/sda1

---

### Post by Andrux101 on 2009-10-07
This HDD is working, I have dual boot - Ubuntu and XP. When I receive that bug, seems that HDD is not reading. How can I edit this menu.lst with this "built-in" commands? Which directory? What is this (initramfs)?

---

### Post by MegaJim on 2009-10-07
boot up with a ubuntu live cd and look at the contents of /boot/grub/menu.lst

It will have a boot entry for your linux install that will define the root hdd using a uuid.  This uuid is placed by udev, however udev isn't working on boot (for whatever reason) so you must specify the hdd using its dev path, which will be something like /dev/sda1 or /dev/sdb3.

You will need to make sure that the device.map file in the same directory is properly resolving your hard drives to appropriate dev paths

if you could post the contents of the following commands, it would help us:

```

cat /boot/grub/menu.lst

```
```

cat /boot/grub/device.map

```
```

cat /etc/fstab

```
```

sudo blkid

```

---

### Post by Andrux101 on 2009-10-07
Oh, now I understand much more! Starting with live cd.. It mean that I download .iso file from [www.ubuntu.com]("http://www.ubuntu.com") and burn in cd as image file? Next, can I live cd start booting from cd in black screens? There menu is only installing ubuntu?!

---

### Post by MegaJim on 2009-10-07
you can try ubuntu without installing it

---

### Post by Andrux101 on 2009-10-09
There are some content of following commands:

[B][I]ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

ubuntu@ubuntu:~$ cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory[/I][/B]

[B][I]ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1250799350797E73" TYPE="ntfs" 
/dev/sda5: UUID="6fa45a36-38b5-495a-8316-3855c55eda71" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="b2c978d6-8caa-4443-9cf8-3d42a336cb93" 

[/I][/B]What to do now?

---

### Post by Andrux101 on 2009-10-09
And this commands.. How can I run this commands on the disk where is installed Ubuntu not on the live cd? I cannot change to installation directories. What can i do?
[B][I]
ubuntu@ubuntu:~$ sudo aptitude reinstall udev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  udev 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 325kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main udev 141-1 [325kB]
Fetched 325kB in 10s (31.9kB/s)                                                 
(Reading database ... 105940 files and directories currently installed.)
Preparing to replace udev 141-1 (using .../archives/udev_141-1_i386.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Processing triggers for man-db ...
Setting up udev (141-1) ...
 * Stopping kernel event manager...                                      [ OK ] 
 * Starting kernel event manager...                                      [ OK ] 
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs is disabled since running on read-only media

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ubuntu@ubuntu:~$ sudo update-initramfs -u -k all
update-initramfs is disabled since running on read-only media
ubuntu@ubuntu:~$ 
[/I][/B]

---

### Post by MegaJim on 2009-10-09
well the disk in your OP is obviously not present on the system anymore which is why its failing.

as /boot/ seems not to be available i would suggest that your boot or root partitions are not mounted

when in the livecd open up my computer and double click each of the drives to have them mounted, then explore its contents to discover the /boot directory and your root partition (/) (you should see /etc /lib /dev and so forth on the root partition)

when you've found the boot partition (it may be the same as root depending on how you installed ubuntu) make sure that your menu.lst file's topmost ubuntu boot stanza has its root parameter pointing at the root drive.

e.g. at the moment it should say something like

```

root=UUID=05d79451-0ad0-43fc-9f51-a2c98b4831f2 ro quiet splash

```

change it to

```

root=/dev/sda5 ro quiet splash

```

the quick way to test if this will work is to edit the topmost boot line in grub such that "root=UUID=05d79451-0ad0-43fc-9f51-a2c98b4831f2 ro quiet splash" is "root=/dev/sda5 ro quiet splash"

To do that, boot up the pc then move the highlighted line to the topmost ubuntu entry and hit the 'e' key, then hit the 'e' key on the appropriate line.

Then you should be able to boot the system and we can continue from there.

---

### Post by Andrux101 on 2009-10-09
**I will try this commands but first, my menu.lst in the /boot/grub looks like that:**

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
# kopt=root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6fa45a36-38b5-495a-8316-3855c55eda71

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=6fa45a36-38b5-495a-8316-3855c55eda71 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6fa45a36-38b5-495a-8316-3855c55eda71
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
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by MegaJim on 2009-10-09
you could also try reading this thread: [http://ubuntuforums.org/showthread.php?t=433710](http://ubuntuforums.org/showthread.php?t=433710)

---

### Post by Andrux101 on 2009-10-09
Yess!!! I solved my problem with this thread: [http://ubuntuforums.org/showthread.php?t=433710](http://ubuntuforums.org/showthread.php?t=433710)

1. Boot LiveCD
2. create /media/newroot/ and mount / on HD  to it (in my case/dev/sda5) 
     Code:
     mkdir /media/newroot/
mount /dev/sda5 /media/newroot/ 
3. chroot to /media/newroot/
     Code:
     chroot /media/newroot/ 
4. update and dist-upgrade
     Code:
     apt-get update
apt-get dist-upgrade

---

### Post by SonicLizzz on 2010-09-03
Hello, I have this very problem myself, but the solution you guys have come up with is not possible for me to complete, because though I can boot from the Live CD, it will not let me use the root user and I can not find the menu.lst other places. Please help!

---

### Post by pcwww on 2010-09-08
> **Andrux101 said:**
> And this commands.. How can I run this commands on the disk where is installed Ubuntu not on the live cd? I cannot change to installation directories. What can i do?
[B][I]
ubuntu@ubuntu:~$ sudo aptitude reinstall udev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  udev 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 325kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main udev 141-1 [325kB]
Fetched 325kB in 10s (31.9kB/s)                                                 
(Reading database ... 105940 files and directories currently installed.)
Preparing to replace udev 141-1 (using .../archives/udev_141-1_i386.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Processing triggers for man-db ...
Setting up udev (141-1) ...
 * Stopping kernel event manager...                                      [ OK ] 
 * Starting kernel event manager...                                      [ OK ] 
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs is disabled since running on read-only media

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ubuntu@ubuntu:~$ sudo update-initramfs -u -k all
update-initramfs is disabled since running on read-only media
ubuntu@ubuntu:~$ 
[/I][/B]
Yes!!! I solved my problem with this method~~~~~THX!!!!!!:popcorn:

---

### Post by BanannaButt on 2010-09-14
> **Andrux101 said:**
> Yess!!! I solved my problem with this thread: [http://ubuntuforums.org/showthread.php?t=433710](http://ubuntuforums.org/showthread.php?t=433710)

1. Boot LiveCD
2. create /media/newroot/ and mount / on HD  to it (in my case/dev/sda5) 
     Code:
     mkdir /media/newroot/
mount /dev/sda5 /media/newroot/ 
3. chroot to /media/newroot/
     Code:
     chroot /media/newroot/ 
4. update and dist-upgrade
     Code:
     apt-get update
apt-get dist-upgrade

I tried doing this, and I am still struggling with things over here.  If you are rather new to Linux (like me), then I might suggest copy-pasting the code in to your terminal by CTRL C and then right-click-pasting in to your terminal.  I could never get the ```
sudo chroot /media/newroot/
``` to work and got the following message: 

```
root@ubuntu:/home/ubuntu# chroot /media/newroot/
chroot: cannot run command `/bin/bash': No such file or directory

```

I tried proceeding with the updates only to find the same error once again when booting up.

Grrr.  Maybe that's a little too much of an understatement to describe my frustration at Linux right now.  Why would you release a buggy kernel update??

---

### Post by Exvin on 2010-09-27
Andrux101's trick did it for me!

As mentioned before, also check out this thread, especially the last post by skrat:

[http://ubuntuforums.org/showthread.php?t=433710](http://ubuntuforums.org/showthread.php?t=433710)

---

### Post by dealson on 2010-09-29
The solution to this problem just worked like magic. 
I thought i was going to re-install my os. 

Thanks team. 
Any one still struggling to have this work, you are probably not yet mounting your /boot partition. 
fdisk -l will be of much help for you to determine which partition you should mount. 

cheers and thanks team

---

### Post by seoras on 2010-10-11
> **MegaJim said:**
> well the disk in your OP is obviously not present on the system anymore which is why its failing.

as /boot/ seems not to be available i would suggest that your boot or root partitions are not mounted

when in the livecd open up my computer and double click each of the drives to have them mounted, then explore its contents to discover the /boot directory and your root partition (/) (you should see /etc /lib /dev and so forth on the root partition)

when you've found the boot partition (it may be the same as root depending on how you installed ubuntu) make sure that your menu.lst file's topmost ubuntu boot stanza has its root parameter pointing at the root drive.

e.g. at the moment it should say something like

```

root=UUID=05d79451-0ad0-43fc-9f51-a2c98b4831f2 ro quiet splash

```

change it to

```

root=/dev/sda5 ro quiet splash

```

the quick way to test if this will work is to edit the topmost boot line in grub such that "root=UUID=05d79451-0ad0-43fc-9f51-a2c98b4831f2 ro quiet splash" is "root=/dev/sda5 ro quiet splash"

To do that, boot up the pc then move the highlighted line to the topmost ubuntu entry and hit the 'e' key, then hit the 'e' key on the appropriate line.

Then you should be able to boot the system and we can continue from there.

I have also experienced this problem (*udevadmn trigger is not permitted while udev is unconfigured*) and have tried all the suggested fixes in the forum. The one that worked, or at least partially was editing /boot/grub/menu.lst and changing  **root=UUID=321b1128-2e39-4f8b-a16c-15c361b901b6** to **root=/dev/sda5 **

This at least allowed me to boot the system and get back to work. I have also reinstalled udev, Unfortunately the system still hangs at boot with the message (*udevadmn trigger is not permitted while udev is unconfigured*) for a while before eventually booting correctly so the problem has not been fully corrected.

Does anyone have any suggestions as to how his can be fixed?

---

### Post by yoramdavid on 2010-12-19
I am having the same problem. At about half way through installing, after downloading all the files needed (after the "apt-get upgrade" command), it tells me not enough space. But there is space, I have 128Mb free on the /boot partition and 1.5 Gb on the /Ubuntu partition. Swap is 1.23 Gb.

I cannot do the initramfs update. It does not work.

With the chroot /media/newroot I get the error "cannot run command '/bind/bash': no such file or directory"

I tried from both a USB drive and from a CD.

Any help is welcome, thanks.

Update:
I realized a "File System" drive (folder (inode/directory) was created during this process which gets out of space.
Location: computer:///, Volume: unknown.
Is there something I am doing wrong?

---

### Post by Mecasickle on 2010-12-21
I'm stilling getting bugged by the chroot error.

I've tried the sudo fdisk -l command, and have rebooted my laptop various times trying with all of the partitions I have (sda1,sda2,sda3), and none of them have a result! It still responds me with :
[B]
chroot: failed to run command `/bin/bash': No such file or directory[/B]

I hate that message ....

Any ideas I'm missing ? ?
Thanks!

---

### Post by DSK on 2011-01-27
Fixed my problem by booting to "System Rescue CD" then running a check with gparted on the drive.

[http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.0.0/systemrescuecd-x86-2.0.0.iso/download](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.0.0/systemrescuecd-x86-2.0.0.iso/download)

Gparted fixed a bunch of "orpaned inodes" then everything booted fine again.

---

