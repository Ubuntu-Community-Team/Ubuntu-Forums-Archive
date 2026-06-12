---
title: "ACPI Question"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by brokenflea on 2005-04-29
i have hoary running on an old thinkpad i1300 and i'm trying to get acpi to work on it. everytime i select "Suspend the computer" from the Log Out option under system my screen stays the same it doesn't blank out, but when i try to click on an application it just freezes and doesn't open up anything at all. and then i have to manually shut the computer down by turning the power off. here's what my /etc/default/acpi-support looks like:

```

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
# was mem
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. It should look something like MODULES="e1000 ipw2100"
MODULES="wg511v2"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

``` 


and here's what my menu.list file looks like in /etc/grub:

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 resume=/dev/hda5 ro

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 resume=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 resume=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```


any help with this would be gladly appreciated. 

TIA

---

### Post by luca_linux on 2005-04-30
Try to pass this kernel parameter: acpi_sleep=s3_bios

---

### Post by brokenflea on 2005-04-30
no luck with that either. changed
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 resume=/dev/hda5 ro quiet splash

to:

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 acpi_sleep=s3_bios ro quiet splash

in menu.lst

and still no luck

everytime i click on suspend from the log out menu the screen just stays there on the desktop and i can't bring it off. i have to press the power button and wait for it to turn off.

---

### Post by malmjako on 2005-10-18
Try changing some of the settings in /etc/default/acpi-support. For instance, try standby instead of mem, which works better for me. (Beware, though. The computer uses more energy in standby mode than in mem mode). Also try commenting POST_VIDEO, SAVE_VBE_STATE and USE_DPMS, one at a time to find a working conifguration for your laptop.

I have (on my HP Omnibook 6000):
```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=standby
MODULES=""
MODULES_WHITELIST=""
#SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
#POST_VIDEO=true
USE_DPMS=true
# RADEON_LIGHT=true
# DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
DISABLE_DMA=true
# RESET_DRIVE=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=true
```

(Side note: In breezy, LOCK_SCREEN seems to have no effect. My laptop is always UNLOCKED on resume, which is a bit scary, I think...)

---

