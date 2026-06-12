---
title: "Weird behavior on boot / shutdown"
date: 2008-09-09
forum: General Help
---

### Post by dai_vernon on 2008-09-09
A few issues:

1) Startup manager won't let me set the startup resolution (grup etc's resolution) to my correct resolution)

2) I don't have 'show text on boot' checked in startup manager, yet the ubuntu splash's progress bar bounces back and forth for a few moments and then switches to text mode.

3) When shutting down, the ubuntu splash progress bar thing is in a bizaare rainbow garble of colors.

Why might this be?

---

### Post by Elfy on 2008-09-09
Not sure about the resolution in startup and shutdown. But might be able to help with the non quiet thing, recently dealt with it myself.

Can you run these in a terminal and post the outputs you get, please surrround each with seperate [noparse]```

```[/noparse] tags

```
cat /boot/grub/menu.lst
cat /etc/initramfs-tools/conf.d/resume
sudo blkid
```

---

### Post by dai_vernon on 2008-09-09
cat /boot/grub/menu.lst
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
# kopt=root=UUID=feb6854d-1a90-4b07-a955-a12e1c6f46aa ro

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
# defoptions=splash vga=771 quiet

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=feb6854d-1a90-4b07-a955-a12e1c6f46aa ro quiet splash vga=769 usbcore.autosuspend=-1
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=feb6854d-1a90-4b07-a955-a12e1c6f46aa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
cat /etc/initramfs-tools/conf.d/resume
```
RESUME=UUID=0540fdb5-93ad-46a9-aa60-1130c1d65180
```

sudo blkid
```
/dev/sda5: UUID="feb6854d-1a90-4b07-a955-a12e1c6f46aa" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f7f0f0a3-3048-4ab0-a69a-51dda8b40494"

```
I can see that that first UUID doesn't match the other two - what is the significance of that?

---

### Post by Elfy on 2008-09-09
That you get verbose text on boot - I would guess that at somepoint you've changed the swap partition somehow, easy fix change the resume on to match the blkid, 

```
sudo nano -B /etc/initramfs-tools/conf.d/resume
```
 change to f7f0f0a3-3048-4ab0-a69a-51dda8b40494

Ctrl+O, enter, Ctrl+X

Regards the shutdown graphic issue I believe it to be a resolution issue.

Edit you could try to remove vga=769 from the kernel line

```
sudo nano /boot/grub/menu.lst
```

If that sorts the colours on shutdown - remove it from the defoptions line

---

### Post by dai_vernon on 2008-09-09
I have indeed changed the swap partition - shrunk it and moved it when I removed windows vista from this machine.  Thanks - rebooting now to check.

---

### Post by dai_vernon on 2008-09-09
No dice - I'm still getting a verbose boot.  Any ideas?

---

### Post by dai_vernon on 2008-09-09
Removing the vga=769 got rid of the garbled graphic on shutdown - thanks!

---

### Post by Elfy on 2008-09-09
You could check that your swap UUID is correct in fstab

```
sudo nano -b /etc/fstab
```

should be > f7f0f0a3-3048-4ab0-a69a-51dda8b40494

Did you catch the edit I made to #4 - aah yes you did :)

---

### Post by dai_vernon on 2008-09-09
It's correct in fstab - I went through a whole spiel when I changed my swap where it would default to off, and I needed to change its UUID in fstab.  I verified it to be sure.

---

### Post by Elfy on 2008-09-09
If you're sure that you have changed it correctly in /etc/initramfs-tools/conf.d/resume then I would be looking to see if there were any problems when it booted then.

Check your logs and watch the screen when it boots - admin >system menu - system logs

---

### Post by dai_vernon on 2008-09-09
> **forestpixie said:**
> If you're sure that you have changed it correctly in /etc/initramfs-tools/conf.d/resume then I would be looking to see if there were any problems when it booted then.

Check your logs and watch the screen when it boots - admin >system menu - system logs

I checked /etc/initramfs-tools/conf.d/resume with nano as root and the UUID there is the same one from here.  I don't notice anything specific with my boot but I'll look again.

Would filming the boot and posting it somewhere help?

What about looking in my logs etc for the boot process and just posting the relevant parts?  Would that be dangerous?

---

### Post by Elfy on 2008-09-09
Before you do this, open dmesg and search for fail - gedit /var/log/dmesg

You could enable the bootlog reboot and see what it says, if anything.

If the file is quite big then I would disable it again afterwards

Open the file ```
sudo nano -B /etc/default/bootlogd
```
change BOOTLOGD_ENABLE=No to Yes

The log should be in /var/boot/log


from [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by dai_vernon on 2008-09-09
The only instance of 'fail' in /var/log/dmesg was 

[   14.364765] Failure registering capabilities with primary security module.

I enabled the bootlog thing - rebooting now to see what happens.

---

### Post by dai_vernon on 2008-09-09
I haven't even got a folder called /var/boot/; file called /var/log/boot is a text file that says

(Nothing has been logged, yet.)

---

### Post by Elfy on 2008-09-09
Looking at the thread - it seems that it the dmesg file now - so chnage the file back to =No

Have you checked the other logs in system log viewer I think it is called - sys >Admin menu.

Other than that not sure at the moment, will look again later...

---

### Post by dai_vernon on 2008-09-09
I looked there but its giant and didn't know what to look for.  Don't worry about it - I haven't got anymore time to throw at this right now.  You've been a big help.

---

