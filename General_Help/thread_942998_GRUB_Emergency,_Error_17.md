---
title: "GRUB Emergency, Error 17"
date: 2008-10-09
forum: General Help
---

### Post by cha0sthe0ry on 2008-10-09
I have been trying to do two things:

Make splash show up again after being previously disabled (didn't make boot any faster)

Add selection on GRUB menu for Slackware which I just installed on a new partition.

I was just asking about an hour ago how to do the slackware thing, and someone suggested the GRUB Howto.  Problem is, I didn't know where to look in there to find what I needed.  So I probably did the wrong thing.

I reinstalled the grub on my MBR.  Now everything except Windows gives me an error 17, "Cannot mount selected partition."  If I press e, and edit in the right partition (hd0,2), it hangs on the splash screen and the screen will go black after about 30 seconds.

*EDIT:  These are my partitions:
(hd0,0)  Windows
(hd0,1)  Linux Swap
(hd0,2)  Ubuntu
(hd0,3)  Slackware*

Getting the GRUB to boot Linux successfully with the splash is #1 priority, other than that, Slackware is on hd0,4 if anyone knows how to add that.


This is my menu.lst:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-6-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro  single
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=cacc4475-9cd0-476a-9dc5-4feee0557746 ro splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microjunk Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Thanks in advance

---

### Post by cha0sthe0ry on 2008-10-09
New update, I changed the boot partitions in all the Ubuntu instances to (hd0,2) from (hd0,0).  Now the boot sequence shows splash, but the screen goes black and gives following error:

Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing Modules (cat /proc/modules: is /dev)
ALERT! /dev/disk/by-uuid/c8acb88f-fb57-4ebc-ba34-74de446a21e0 does not exist. Dropping to a shell!

What does this mean, and how do I fix that?

---

### Post by caljohnsmith on 2008-10-09
One thing I notice is that your UUIDs for Ubuntu are not consistent:
> ```
title Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-6-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro quiet splash
initrd /boot/initrd.img-2.6.27-6-generic
quiet

title Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-6-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro single
initrd /boot/initrd.img-2.6.27-6-generic

title Ubuntu intrepid (development branch), kernel Last successful boot
root (hd0,0)
kernel /boot/last-good-boot/vmlinuz root=UUID=[COLOR="Red"]cacc4475-9cd0-476a-9dc5-4feee0557746[/COLOR] ro splash last-good-boot
initrd /boot/last-good-boot/initrd.img
quiet

title Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c8acb88f-fb57-4ebc-ba34-74de446a21e0 ro single
initrd /boot/initrd.img-2.6.24-19-generic
```
That may not fix your problem, but it is something that would be worth fixing. From you Live CD you can check to see which UUID is correct:
```
sudo blkid
```
And look for your Ubuntu partition, and make sure the UUID in menu.lst matches blkid's output.

---

### Post by cha0sthe0ry on 2008-10-09
Process of elimination shows me the one that is different is correct, because it loaded correctly, so I changed them all to that UUID, and what do you know, they all work now!  Thanks!

However that is only the part of the problem I worsened today.  The problem is that I still don't have a splash screen, and it is bothering me because I don't remember it being this hard to take the usplash off.  Can anyonw look at this menu.lst and tell me what needs to be changed to get the usplash to work for the entire boot up process?  Right now it is showing a splash screen for part of the process, and below the loading bar it is still displaying text boot lines.  How do I fix that part anyone?

---

### Post by phidia on 2008-10-09
There is a customization guide for usplash [here]("https://help.ubuntu.com/community/USplashCustomizationHowto"). That is for earlier releases but it provides some useful info I think.

---

### Post by jithin1987 on 2008-10-14
I had this problem after i rearranged my partitions. My grub was screwed and I had to reinstall grub but after that Last Successful Boot entry was no longer there in the grub menu.
Can any one tell me what I should do to get it back?

---

### Post by unutbu on 2008-10-14
jithin1987, please post the information requested in steps 3--5: [http://ubuntuforums.org/showpost.php?p=5584686&postcount=465](http://ubuntuforums.org/showpost.php?p=5584686&postcount=465)

---

### Post by jithin1987 on 2008-10-14
Output of sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff266e6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3355    26949006    7  HPFS/NTFS
/dev/sda3            3356        3616     2096482+  82  Linux swap / Solaris
/dev/sda4            3617        9729    49102672+   5  Extended
/dev/sda5            3617        9729    49102641   83  Linux


title           Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=1587386b-5227-43bf-9d4c-7716b255e664 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=1587386b-5227-43bf-9d4c-7716b255e664 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu intrepid (development branch), memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

cat /boot/grub/menu.lst
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

blkid

/dev/sda1: UUID="3CE443B0E4436B6A" TYPE="ntfs"
/dev/sda2: LABEL="/" UUID="e698cd18-0062-4a74-b2f1-72c68ff2ab5e" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: TYPE="swap" UUID="e6afa0b7-1339-48b7-85d2-08ea91b5212d"
/dev/sda5: UUID="1587386b-5227-43bf-9d4c-7716b255e664" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: UUID="1587386b-5227-43bf-9d4c-7716b255e664" TYPE="ext3"
/dev/loop0: TYPE="squashfs"

---

### Post by unutbu on 2008-10-14
Type
```

sudo update-grub
```
According to [https://wiki.ubuntu.com/KernelTeam/removing-old-kernels](https://wiki.ubuntu.com/KernelTeam/removing-old-kernels)
a "Last successful boot entry" is made by running this command.

---

### Post by jithin1987 on 2008-10-14
I did that but still I dont have last good boot in my menu.lst

---

### Post by unutbu on 2008-10-14
According to [https://wiki.ubuntu.com/KernelTeam/removing-old-kernels](https://wiki.ubuntu.com/KernelTeam/removing-old-kernels)
"Last-good-boot is implemented fully in Intrepid/8.10 now."

So are you running update-grub from an Intrepid/8.10 system?

---

### Post by cha0sthe0ry on 2008-10-14
> **phidia said:**
> There is a customization guide for usplash [here]("https://help.ubuntu.com/community/USplashCustomizationHowto"). That is for earlier releases but it provides some useful info I think.

Thank you, that was what I needed, I had to specify a resolution on the defoptions line.

---

### Post by jithin1987 on 2008-10-14
yes i use kubuntu 8.10 intrepid beta

---

### Post by jithin1987 on 2008-10-14
One more thing as I told before that I have been resizing my intrepid partition by removing others and increasing the size of ubuntu partition. Then I had to re install grub from a live cd and edited the menu.lst file to change root to hd0,4 from hd0,5 to remove  the grub 17 error. I have an entry in menu.lst which is still hd0,5

## default grub root device
## e.g. groot=(hd0,0)      
# groot=(hd0,5)

What does this entry do. Could that be the problem?

Another issue i see is that i have 2.6.27-4 kernel installed but update-grub is not adding them to menu.lst( i manually removed them before). I see another entry in menu.lst
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

Can u please explain me what this does?

---

### Post by jithin1987 on 2008-10-14
I changed groot to hd0,4 my root and then update-grub identifies the 2.6.27-4 my old kernel. But still there is no last good boot entry. And I do not have a /boot/last-good-boot directory as mentioned in the menu.lst posted in this thread

Is my problem related to this bug [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/251540](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/251540) ? I didn't understand it much.

---

### Post by cha0sthe0ry on 2008-10-15
> **jithin1987 said:**
> I changed groot to hd0,4 my root and then update-grub identifies the 2.6.27-4 my old kernel. But still there is no last good boot entry. And I do not have a /boot/last-good-boot directory as mentioned in the menu.lst posted in this thread

Is my problem related to this bug [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/251540](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/251540) ? I didn't understand it much.

Jithin1987, I think you are better off probably starting your own topic in general help.  Not a lot of people are going to be looking at this anymore.  It took me a few posts to get the answer I needed.  I personally don't know enough to help you, unfortunately, so I would start my own topic if I were you.

---

