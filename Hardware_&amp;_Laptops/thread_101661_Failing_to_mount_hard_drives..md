---
title: "Failing to mount hard drives."
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by aicrono on 2005-12-10
Last night I was rearraging my room around and once I was finished I hook my computer back up, and now my Ubuntu box refused to mount my hard drive. I have checked and made sure all the cables are sercure. When I turn on my computer, it appears to start booting fine, it brings up the the boot screen, telling me its loading the modules, then those load, then it says mounting root something, but switches to another screen quickly. I have been using Ubuntu since about June or so this year, and have been using Breezy since the official release of it. 

Here is what the screen it switched to says:

```
Booting 'Ubuntu, kernel 2.6.12-10-386'

root   (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x124cd9]
initrd /boot/initrd.img-2.6.12-10-386
   [Linux-initrd @ 0x1fae3000, 0x50cf9a bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...
FATAL: Module minix not found.
mount: Mounting /dev/hda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount:/dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#
```

---

### Post by taurus on 2005-12-10
I am still trying to understand how rearranging your room effects your harddrive because I move my computers around all the time...  Since it drops you into a prompt, see if you can mount /dev/hda1 by hand.  Maybe you need to look at your /etc/fstab and /boot/grub/grub.lst again!!!  Otherwise, display the output of 

fdisk -l /dev/hda

---

### Post by aicrono on 2005-12-10
I am also still trying to see why it would effect anything, as I have also moved my room around alot too, but this is the first time that this has ever happened to me.

Anyways, I ran mount /dev/hda1 and this came up
```
# mount /dev/hda1 
mount:
Cannot read /etc/fstab: No such file or directory
```

Alright that didnt work, now I ran fdisk -l /dev/hda and this is what pops up

```
# fdisk -l /dev/hda
/bin/sh: fsdisk: not found
```

And when I go to /etc/ all that is in there is 'udev' and 'modprobe.d'.

---

### Post by taurus on 2005-12-10
Try mounting with 

mount -t ext3 /dev/hda1 /
(assuming you use ext3 filesystem for your /dev/hda1)

Once it's mounted, maybe you want to modify your /boot/grub/grub.lst to make it look something like

real_root=/dev/hda1 
instead of 
root=/dev/hda1

---

### Post by aicrono on 2005-12-10
```
# mount -t ext3 /dev/hda1
mount
Cannot read /etc/fstab: No such file or directory
```

No luck still, =\. And thanks for trying help. =)

---

### Post by taurus on 2005-12-10
Which one did you try

mount -t ext3 /dev/hda1 
-or-
mount -t ext3 /dev/hda1 /

Try running the second option, instead!

mount -t ext3 /dev/hda1 /

Otherwise, what is the output of this command,

ls -la

---

### Post by aicrono on 2005-12-10
Oops, definetly didn't notice that "/" at the end. Alright I ran mount -t ext3 /dev/hda1 /

```
# mount -t ext3 /dev/hda1
# 
```

I am assuming it mounted. And as for changing my /boot/grub/grub.lst, there is no boot folder, so do I need to go to my grub menu, like right when my pc boots up before loading the kernel?

And as for ls -la
```
# ls -la
drwxr-xr-x  4 0       0             0 udev
drwxr-xr-x  2 0       0             0 modprobe.d
drwxr-xr-x 22 0       0          4096 ..
drwxr-xr-x  4 0       0             0 .
```

---

### Post by taurus on 2005-12-10
What is the output of this command?

df

Since you decided to have only one partition for Ubuntu, /, it means that /boot should be under /...

---

### Post by aicrono on 2005-12-10
```
# df
/bin/sh: df: not found
```

As for the folders in /

```
# cd /
# ls
dev bin etc modules scripts usr proc var root conf lib sbin init sys tmp
```

Edit: Normally, I would just reformat if anything like this happened, but I had important stuff I need to keep on here right now

---

### Post by taurus on 2005-12-10
How did you setup your harddrive?  Did you create one partition for Ubuntu and one for swap or did you have one partition for /, one for /boot, and one for swap, etc.?

---

### Post by aicrono on 2005-12-10
I did what ever the default for the Breezy's installation was, which I think is one for Ubuntu and one for swap.

---

### Post by taurus on 2005-12-10
Do you have a LiveCD handy somewhere?  Maybe you need to use it to boot your machine and mount your /dev/hda1 somewhere and have a look at both /etc/fstab & /boot/grub/grub.lst to see what's wrong with them...

---

### Post by aicrono on 2005-12-10
I have the Kubuntu live cd sitting around here somewhere, but that was for my 64bit machine... I guess I could just download it, shouldn't take too long.

---

### Post by taurus on 2005-12-10
Yeah, it's handy to have a LiveCD of some kind around in case you may want to use to it fix your sick machine!  I always have KnoppixCD with me either at home or at work...  ;)

---

### Post by aicrono on 2005-12-10
Thanks a lot again  for you help, I am currently downloading the live cd.

---

### Post by taurus on 2005-12-10
If you have a DSL, it would probably take you a little over an hour but if you have a fast connection (like I have at work), it would take about 25 minutes or less!  :D

---

### Post by aicrono on 2005-12-10
Already downloaded it and got it burned ;).

---

### Post by aicrono on 2005-12-10
Alright sorry for delay, for some reason gedit refused to open. Alright I am just going to post my fstab since I am not sure how it is supposed too look. :oops: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

And as for /etc/grub/grub.lst, it's not here. =(

---

### Post by taurus on 2005-12-10
Actually, it's /boot/grub/grub.lst, not /etc/grub/grub.lst!

---

### Post by aicrono on 2005-12-10
Agh! I am all over typo's and misreading things today, I was actually in /boot/grub/. :oops: Sorry about that.

Here is all that is in my /boot/grub/.

```
ubuntu@ubuntu:~/Desktop/boot/grub$ ls
device.map     fat_stage1_5  menu.lst   minix_stage1_5     stage1  xfs_stage1_5
e2fs_stage1_5  jfs_stage1_5  menu.lst~  reiserfs_stage1_5  stage2
ubuntu@ubuntu:~/Desktop/boot/grub$

```

---

### Post by taurus on 2005-12-10
Okay, what does menu.lst say,

more menu.lst

and also the output of this as well, just in case,

fdisk -l /dev/hda

---

### Post by aicrono on 2005-12-10
Here is menu.lst

```
ubuntu@ubuntu:~/Desktop/boot/grub$ more menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And as for fdisk -l /dev/hda (had to use sudo because it wouldn't open with out it)
```
ubuntu@ubuntu:~/Desktop/boot/grub$ sudo fdisk -l /dev/hda

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14379   115499286   83  Linux
/dev/hda2           14380       14946     4554427+   5  Extended
/dev/hda5           14380       14946     4554396   82  Linux swap / Solaris

```

---

### Post by taurus on 2005-12-10
Yes, you have to use "sudo" to run the fdisk command.  In your /boot/grub/menu.lst, change the line that reads "root=/dev/hda1" to "real_root=/dev/hda1" and reboot...  Hopefully, that would cure the problem that you have!

---

### Post by aicrono on 2005-12-10
Well, still not working =(. But this time it gave a different error.

```
Booting 'Ubuntu, kernel 2.6.12-10-386'

root   (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.12-10-386 real_root=/dev/hda1 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x124cd9]
initrd /boot/initrd.img-2.6.12-10-386
   [Linux-initrd @ 0x1fae3000, 0x50cf9a bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...
/dev/cdrom: open failed: No medium
No volume groups found
DosSegMgr: Warning: Using an alternate geometry (Cylinders, Heads, Sectors) for drive hda.
The kernel reported drive geometry is: C= 65535 H=16 S=63
The partition records report a geometry of: C=65535 H=255 S=63
Using the alternate geometry reported by the shell partition records.
ALERT! does not exsist. Dropping to a shell!

BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#
```

---

### Post by taurus on 2005-12-10
It looks to me from the error message that there is something funny going on with your harddrive!  Have you looked into the BIOS to make sure you have set it to "auto" for your master drive--first HD?

---

### Post by aicrono on 2005-12-10
All I got is one hard drive. =( I typo'd the thread name, and as for bios, it wont let me go to them, as soon as I turn on my computer, its brings up the Gateway thing, then starts booting to grub. But I think I may have found a way to save most of the important stuff. Since I can mount my hard drive succesfully on the live cd, and I can try and connect to one of my other computers at home and transfer some stuff over to there, then reformat, and transfer everything back. Should I give it a go?

---

### Post by taurus on 2005-12-10
I believe you have to hit F12 (or F2) when you hear a beep if you want to get into the BIOS with Gateway machine!  However, if you can save all the important docs from your HD, then probably best to just wipe it off and re-do Ubuntu over again...  Maybe you want to consider having at least three partitions: /, /boot (100MB), and swap (512MB)!!!  And they are can be on primary partitions; they don't have to be in extended partitions...

---

### Post by aicrono on 2005-12-10
Thank you so much for your help, I'd still be stuck on the first error in this thread with out you. I am sending over the important docs right now. And yeah, I think I should make 3 primary partitions this time. I can't thank you enough. :mrgreen: :mrgreen:

---

### Post by taurus on 2005-12-10
No problem at all.  Glad to help even though we couldn't get it to boot!  You can post here or PM me if you have questions...

---

### Post by Jylie on 2006-05-03
Hi

My computer is having the exact same problem.

Did you ever solve this?

I thought it might have been a hardware failure, but I copied the hard drive to another one, but this didn't solve anything.

---

### Post by Jylie on 2006-05-06
Well I solved this problem, but don't ask me how.

My installation was on a 10GB hard drive.  I copied it to a 20GB hard drive using Acronis.  I then tried a reinstallation (on the 20GB hdd), using expert mode, and got stuck around the partitioning stage of installation.  I'm not sure what I actually did, but I was messing around with the partitions.  I wasn't too worried about losing data at this stage as I had the 10GB hdd still, but I was also at a point where I was prepared to lose everything and start again.  Anyway, the installation wouldn't let me continue for some reason to do with the partitions.  I removed the CD and rebooted.  Magically it booted up normally.  WTF!

---

### Post by FurryNemesis on 2006-05-06
I was (trying) to follow the instructions in this thread 
and after nearly killing my laptop ended up with an fstab output like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

I was trying to mount an external ntfs hard drive with write capability as per the thread - in any case I did something wrong and was wondering what line 2 meant as that's where the problem seems to be...

Thanks in advance.

---

