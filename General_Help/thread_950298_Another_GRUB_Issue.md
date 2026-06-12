---
title: "Another GRUB Issue"
date: 2008-10-17
forum: General Help
---

### Post by loaba on 2008-10-17
I am dual-booting Windows and Ubuntu on two separate drives. This configuration has worked in the past, but now, after installing Linux on a new HDD, GRUB does not see the Windows install.

How can I point GRUB to the Windows install?

---

### Post by Pro-reason on 2008-10-17
It seems that the Linux installation did not automatically add an entry for Windows, which would have been preferable.

Please post the results of these commands:

```

cat /boot/grub/menu.lst
sudo blkid

```

---

### Post by /////// on 2008-10-17
In terminal type in gksu gedit /boot/grub/menu.lst then scroll to the bottom where the other OSs are and add:
title           "add what you want displayed when booting here without exclamation marks"
rootnoverify    (hd1,0)
makeactive
chainloader     +1
But make sure to change the line after rootnoverify ie (hd1,0) to the harddisk that you have windows on, note hd1,0 means second hard disk 1 partition which is what I assume you have windows on

---

### Post by loaba on 2008-10-17
Per your request...
```
xxxxxxx@xxxxxxxx:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=1ae79258-81be-4d43-95bb-6b9da8f5ca74 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1ae79258-81be-4d43-95bb-6b9da8f5ca74 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1ae79258-81be-4d43-95bb-6b9da8f5ca74 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1ae79258-81be-4d43-95bb-6b9da8f5ca74 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1ae79258-81be-4d43-95bb-6b9da8f5ca74 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

```
/dev/sda1: UUID="1ae79258-81be-4d43-95bb-6b9da8f5ca74" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f0bdae68-7ef5-469d-a631-988d506e7e40" 
/dev/sdb1: UUID="C46062F76062F01A" TYPE="ntfs"
```

---

### Post by loaba on 2008-10-17
Just for clarification; each OS is on it's own disk.

---

### Post by caljohnsmith on 2008-10-17
Looks like it should be simple to add Windows to your menu.lst. Just do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Let me know how it goes or if you run into problems. :)

---

### Post by Pro-reason on 2008-10-17
Open up the file with the following command:

```

gksu gedit **/boot/grub/menu.lst**

```

After that last section, paste the following lines:

```

### END DEBIAN AUTOMAGIC KERNELS LIST


title           **Windows**
root            (hd1,0)
savedefault
makeactive
chainloader     +1


```

Save and close.

While you're there, you should probably assign a volume label to your Windows drive too.  In the terminal, type these commands:

```

sudo apt-get install **ntfsprogs**
sudo ntfslabel /dev/sdb1 **Windows**

```

This will now enable you to use “LABEL=Windows” instead of “/dev/sdb1” or “UUID="C46062F76062F01A”, in files such as /etc/fstab.

---

### Post by loaba on 2008-10-17
And it works - thanks to both of you!

Now - sub-question - how do I rename the windows drive in Ubuntu?

---

### Post by Pro-reason on 2008-10-17
> **loaba said:**
> And it works - thanks to both of you!

Now - sub-question - how do I rename the windows drive in Ubuntu?

That's a bit surreal.  I just told you how to do that.  I suppose you must have meant to ask how to rename the Ubuntu drive.

Since the drive must be unmounted to rename it, you'll have to boot from a live CD to do this.  Then open a terminal and do this command: 

```

sudo e2label /dev/sda1 Ubuntu

```

---

### Post by loaba on 2008-10-21
I did in fact mean how do I change the label on the NTFS drive - I've read the tutorials but it simply doesn't make sense to me.

I tried the above commands - no go

---

### Post by Pro-reason on 2008-10-22
> **loaba said:**
> I did in fact mean how do I change the label on the NTFS drive - I've read the tutorials but it simply doesn't make sense to me.

I tried the above commands - no go

That's weird.  Open the terminal and paste this into it again:

```

sudo ntfslabel /dev/sdb1 Windows

```

It might require a reboot for this label to stick.  I'm not sure.

The &#8220;sudo blkid&#8221; command should tell you what the current label for that drive is.

---

