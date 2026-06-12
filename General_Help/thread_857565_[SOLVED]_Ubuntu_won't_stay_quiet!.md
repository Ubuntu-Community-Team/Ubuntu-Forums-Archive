---
title: "[SOLVED] Ubuntu won't stay quiet!"
date: 2008-07-12
forum: General Help
---

### Post by pi.boy.travis on 2008-07-12
Hi.  When I boot, I see the Ubuntu splash screen for about two seconds, then I see the infamous boot messages.  I am concerned about this, because according to the start-up manager, Ubuntu should be quiet.  I suspect this has something to do with menu.lst, but I don't know what to do to fix it.  Here it is:

```
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro splash quiet
initrd		/boot/initrd.img-2.6.24-16-generic


title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Any suggestions?

Thanks!

---

### Post by spiderbatdad on 2008-07-12
try editing these two sections as follows:
```
# kopt=root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro --quiet splash
```

```
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro --quiet splash
```

---

### Post by pi.boy.travis on 2008-07-13
Now I don't see a splash screen at all, and I am thinking that the problem is something else because menu.lst appears to be correct.  Here is the "new" menu.lst:

```
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro --quiet splash

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro --quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by spiderbatdad on 2008-07-13
Not sure. Maybe your kernel uses a different syntax than the old 2.6.22 kernel...try removing the -- so you have: ro quiet splash

good luck.

---

### Post by coffeecat on 2008-07-13
You get this problem if the UUID of the swap partition has been changed since you installed Ubuntu. Sometimes something goes wrong in the installation - this happened to me. It's possible this is your problem.

Anyway, have a look at these two threads:

[http://ubuntuforums.org/showthread.php?t=746132&page=2](http://ubuntuforums.org/showthread.php?t=746132&page=2)

[http://ubuntuforums.org/showthread.php?t=782700](http://ubuntuforums.org/showthread.php?t=782700)

and also:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990)

What you have to do is:

1 - Run 'sudo blkid -c /dev/null' (no quotes) from a terminal. Include the -c /dev/null bit. If you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

2 - Check that the UUID for the swap partition in /etc/initramfs-tools/conf.d/resume is the same as the UUID you got from blkid. Edit the file if necessary.

3 - Run 'sudo update-initramfs -u' from a terminal (again, no quotes).

4 - Reboot.

5 - Enjoy usplash.

**EDIT:** As people are thanking me for this post, I ought to add that you must also check the UUID in your /etc/fstab. See my post later in this thread.

---

### Post by pi.boy.travis on 2008-07-13
Thanks a TON!  This really had me stumped.

---

### Post by coffeecat on 2008-07-13
> **pi.boy.travis said:**
> This really had me stumped.

It did me at first. How to fix it is now engraved on my heart. :( Have a look at my /etc/initramfs-tools/conf.d/resume

```
#RESUME=UUID=44f72ff4-9069-4936-88c1-804e4a626322
#RESUME=UUID=7b2b22b9-9ca9-4413-b161-9ab26f598bba
#RESUME=UUID=f3b8c2cc-96df-46ca-a0e9-340fb079d7f6
RESUME=UUID=7a19017d-3ca3-49af-8044-047d7115c52f
```That's because this is a multi-boot and often when I install other distros, they reformat the swap partition. :roll: I keep the old UUIDs as souvenirs. :wink:

---

### Post by VMC on 2008-07-13
Well this has sure been interesting, but not sure where to go from here. This is my outputs from the above commands. The "/etc/initramfs-tools/conf.d/resume" file is different than my blkid and fstab, even after reboot. 

I ran this update and nothing changed:
```
sudo update-initramfs -u
```

> $ [B]sudo blkid -c /dev/null
[/B]
/dev/sda1: UUID="d8533154-cef1-4cce-a823-9f3f74aab65b" TYPE="ext3" 
/dev/sda3: UUID="14663ABF2A6030C0" TYPE="ntfs"
/dev/sda5: TYPE="swap" UUID="ea4ab429-32b2-4152-bf2e-d537f49d7da3"

$ **cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=d8533154-cef1-4cce-a823-9f3f74aab65b / ext3 relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ea4ab429-32b2-4152-bf2e-d537f49d7da3 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

$ **cat /etc/initramfs-tools/conf.d/resume**

RESUME=UUID=0703bda2-3d0b-42e5-9d49-5c2634a4bd53

I think spiderbatdad's comment might be of interest:
Maybe I should add the "--quiet" on the end and change "quite" to "--quite".
"# kopt=root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro"
"# defoptions=splash vga=773 quiet"

Actaually I don't mind the text output. I have never lost my splash screen and wasn't aware of any problems. Just that this has been an interesting read, and the blkid cache, and update of the initramfs were of interest. Not sure what to make of the difference of the initramfs and fstab, regarding the UUID..

---

### Post by unutbu on 2008-07-13
VMC, see [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) (Resuming from Hibernation).
I think /etc/initramfs-tools/conf.d/resume is used for hibernation. Since in your case your resume's UUID does not match swap's UUID, your hibernation probably is not working.

---

### Post by coffeecat on 2008-07-14
> **VMC said:**
> The "/etc/initramfs-tools/conf.d/resume" file is different than my blkid and fstab, even after reboot. 

You have to edit /etc/initramfs-tools/conf.d/resume **yourself**. It doesn't get changed automatically. It's having the wrong UUID in /etc/...../resume that is the problem.

**pi.boy.travis**, just in case you're still following this thread, you also need to check the UUID for the swap partition in your /etc/fstab and make sure it matches the one from blkid. I forgot to mention that because I loathe UUIDs with such a passion that I mercilessly expunge them from my fstab and replace them with the saner /dev/sdax type references.

In **VMC**'s case the fstab UUID is correct, but depending on why this problem arose, it may or may not be for you.

---

### Post by pi.boy.travis on 2008-07-14
Yup, I already updated fstab.

At least we don't have to deal with A drive, C drive, etc.

---

### Post by VitaminG on 2008-07-28
I'm not sure why my system won't cooperate, but this doesn't work. The commands all worked just as they were supposed to, but the splash screen still disappears right as the bar should start filling up. I'm running 2.6.24-19-generic (x86_64), and the only other installed kernel is 2.6.24-16-generic. I even ran 'sudo update-initramfs -u -k all', but still no results. Any ideas?

EDIT: I just tried reformatting my swap and redoing the entire process... it works perfectly now.

---

### Post by staticsage on 2008-08-06
I'm now experiencing this problem with usplash. I've tried all the suggested methods, and nothing worked. If I change usplash.conf down to 1280x800, the splash screen appears, but it does not work with my native resolution (1920x1200). I had never touched the usplash.conf file before and usplash has always worked at 1920x1200.

The UUIDs in my fstab and resume are the same as the one listed in the output of sudo blkid -c /dev/null. (I also have not made any partitions changes, this is a week old install of 8.04.1) I've tried sudo update-initramfs -u, and dpkg-reconfigure usplash and apt-get --purge --reinstall

Any ideas?

---

### Post by coffeecat on 2008-08-08
**staticsage**, I think yours is a different issue. The original problem was that of the usplash disappearing because of a changed swap partition UUID. Your problem seems to be down to monitor resolution and what is appropriate to put in usplash.conf.

You'd be better off starting your own thread, rather than resurrecting this one which has run its course.

---

### Post by Tuxoid on 2008-08-21
I am experiencing the same issue with a disappearing usplash. I have now run 'sudo blkid -c /dev/null', found out what I need to switch th UUID in '/etc/fstab' and '/etc/initramfs-tools/conf.d/resume', and when I run 'sudo update-initramfs -u', it gives this output:

```
cryptsetup: WARNING: found more than one resume device candidate:
                     UUID=975927b6-ffaa-4152-8eca-10d3519b9132
                     UUID=4a905185-718e-4e2d-aac9-6a1603c37f4a
```

It's as if I never changed the UUIDs, when I did. Here, /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d1a1dca-6d2b-436d-b8f3-a24557661442 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4a905185-718e-4e2d-aac9-6a1603c37f4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

and  /etc/initramfs-tools/conf.d/resume:

```
RESUME=UUID=4a905185-718e-4e2d-aac9-6a1603c37f4a
```

Is there any other configuration files that I should be editing. I don't have a clue anymore.

Just for thoroughness, here is my menu.lst, even though it probably doesn't matter:

```
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
default		saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8d1a1dca-6d2b-436d-b8f3-a24557661442 ro

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
# defoptions=quiet splash vga=792

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

title		Ubuntu 8.04.1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8d1a1dca-6d2b-436d-b8f3-a24557661442 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8d1a1dca-6d2b-436d-b8f3-a24557661442 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		test system memory
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Tuxoid on 2008-08-21
I fixed my usplash just now, yet I don't know how... :(

---

### Post by xfacta on 2008-10-22
Coffecats fixes easily fixed my verbose booting, I tested normal boots, hibernation and suspending - all OK.
I have back the swap file as it should be, the reason all this happened was I changed all the HDD's partitioning. I was getting by without the swap file because I have enough RAM and can't seem to fill it, unlike on a Windows box!

---

### Post by PatrickVogeli on 2009-05-01
> **coffeecat said:**
> You get this problem if the UUID of the swap partition has been changed since you installed Ubuntu. Sometimes something goes wrong in the installation - this happened to me. It's possible this is your problem.

Anyway, have a look at these two threads:

[http://ubuntuforums.org/showthread.php?t=746132&page=2](http://ubuntuforums.org/showthread.php?t=746132&page=2)

[http://ubuntuforums.org/showthread.php?t=782700](http://ubuntuforums.org/showthread.php?t=782700)

and also:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990)

What you have to do is:

1 - Run 'sudo blkid -c /dev/null' (no quotes) from a terminal. Include the -c /dev/null bit. If you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

2 - Check that the UUID for the swap partition in /etc/initramfs-tools/conf.d/resume is the same as the UUID you got from blkid. Edit the file if necessary.

3 - Run 'sudo update-initramfs -u' from a terminal (again, no quotes).

4 - Reboot.

5 - Enjoy usplash.

**EDIT:** As people are thanking me for this post, I ought to add that you must also check the UUID in your /etc/fstab. See my post later in this thread.
Just here to say a huge to say: THANK YOU!

I've been having trouble with dissapearing usplash and it seems it has been that way since I installed debian 5.0.1, which formated my swap partition. It seems Debian used something older than ubuntu, since the partition didn't have and UUID. Re-formating it in ubuntu and doing as you said has fixed it... thanks :)

---

### Post by pbubenik on 2009-05-22
None of the above worked for me, but I found the following solution on another thread.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/22658/comments/6](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/22658/comments/6)

The problem was that usplash timed out during the file system check (checkfs). This seems to happen if you have multiple drives and/or partitions.

The solution is to increase the splash timeout before checkfs.

Create the file /etc/rcS.d/S29usplash_timeout.sh
with the following two lines in it:

#!/bin/sh
/sbin/usplash_write "TIMEOUT 60"

I think you also need the make the file executable with

sudo chmod 744 /etc/rcS.d/S29usplash_timeout.sh

---

