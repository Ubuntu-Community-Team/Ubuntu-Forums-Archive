---
title: "dual boot fail?"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by efefach on 2009-08-06
Hey guys, I've been reading ubuntu-related stuff for a while, and finally decided to install it a few days ago. However, windows xp doesn't boot anymore. :confused:
 I followed these instructions: [http://apcmag.com/how_to_dual_boot_w...lled_first.htm]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")
and everything was smooth and great. However, when I rebooted it and wanted to load windows xp, it would say “starting up . . .” and not boot. Ubuntu still loads fine (using it right now). Does anyone know what to do? Thanks for helping out a newbie. Much appreciated. [IMG]http://forum.notebookreview.com/images/smilies/smile.gif[/IMG] 

Here's a few pictures. I took it with the palm pre, so it might be a bit blurry. 

 [[IMG]http://img193.imageshack.us/img193/5673/cimg0023z.th.jpg[/IMG]]("http://img193.imageshack.us/i/cimg0023z.jpg/")   [[IMG]http://img248.imageshack.us/img248/7879/cimg0024.th.jpg[/IMG]]("http://img248.imageshack.us/i/cimg0024.jpg/")  [[IMG]http://img156.imageshack.us/img156/1271/cimg0019o.th.jpg[/IMG]]("http://img156.imageshack.us/i/cimg0019o.jpg/")

I posted this problem on the linux section on notebookreview, but they couldn't figure it out. [http://forum.notebookreview.com/showthread.php?t=406158](http://forum.notebookreview.com/showthread.php?t=406158)
Hopefully you guys can help me out?? Thanks.

---

### Post by DracoMoye on 2009-08-06
what do you add to /boot/grub/menu.lst

---

### Post by merlinus on 2009-08-06
Open a terminal and post results of these commands:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by efefach on 2009-08-07
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c6d57ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25177   202234221    7  HPFS/NTFS
/dev/sda2           25178       30401    41961780    5  Extended
/dev/sda5           25178       30181    40194598+  83  Linux
/dev/sda6           30182       30401     1767118+  82  Linux swap / Solaris

``````
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
# kopt=root=UUID=a1271e48-4cda-4d26-a0eb-4bf5a5d41e76 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a1271e48-4cda-4d26-a0eb-4bf5a5d41e76

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        a1271e48-4cda-4d26-a0eb-4bf5a5d41e76
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a1271e48-4cda-4d26-a0eb-4bf5a5d41e76 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        a1271e48-4cda-4d26-a0eb-4bf5a5d41e76
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a1271e48-4cda-4d26-a0eb-4bf5a5d41e76 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a1271e48-4cda-4d26-a0eb-4bf5a5d41e76
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a1271e48-4cda-4d26-a0eb-4bf5a5d41e76 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a1271e48-4cda-4d26-a0eb-4bf5a5d41e76
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a1271e48-4cda-4d26-a0eb-4bf5a5d41e76 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a1271e48-4cda-4d26-a0eb-4bf5a5d41e76
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


```Thanks for the replies!

---

### Post by merlinus on 2009-08-07
The xp entry in menu.lst is correct, so something else must be amiss.

Try supergrub to see if you can boot xp:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by efefach on 2009-08-07
ok i'll check it out. thanks a lot!

---

### Post by oldfred on 2009-08-07
Delete the makeactive line in your windows entry. makeactive should only be used with the root command.

I have two versions, both work. The root is from my updated 32 bit version and rootnoverify is from a clean install of 64 bit ubuntu.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

Or:
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by presence1960 on 2009-08-07
If you still can't get it run windows download the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") to your desktop. Open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file here. When pasted here highlight all text and click the # sign on the toolbar to place code tags around the text. This info will give us a more in depth look at your setup and boot process. it is more comprehensive than running multiple commands from terminal

---

