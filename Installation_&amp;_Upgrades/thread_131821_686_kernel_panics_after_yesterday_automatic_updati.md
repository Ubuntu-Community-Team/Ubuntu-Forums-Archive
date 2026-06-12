---
title: "686 kernel panics after yesterday automatic updating"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by Tibor60 on 2006-02-17
yesterday night I allowed to install the automatic updates. All seemed to go OK, I halted the PC as usual. Today morning I could not boot to my usual 
2.6.12-10-686 kernel:
Ramdisk: run out of compressed data
Invalid compressed format (err=1)
Kernel panic - not syncing:VFS:unable to mount root fs on unknown - block(0,0)

In recovery mode some additional error mesages:
VFS:cannot open root device "hda5" or unknown block(0,0)
Please append a correct "root=" boot option

With the 2.6.12-10-386 kernel  I can boot to my system without problem...
Is it a bug or I should something do with the configfiles?

Please help!
Tibor

---

### Post by abhaysahai on 2006-02-17
Please post your grub/menu.lst

---

### Post by Tibor60 on 2006-02-17
timeout 10


title		Ubuntu, kernel 2.6.12-10-686 
unhide		(hd0,0)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet splash hdc=cdrom hdd=cdrom
initrd		/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
unhide		(hd0,0)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.12-10-686
boot

title		Ubuntu, memtest86+
unhide		(hd0,0)
root		(hd0,1)
kernel		/memtest86+.bin  
boot

title		Windows XP Professional
unhide          (hd0,0)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		UHU Linux
configfile	(hd1,0)/boot/grub/menu.lst

# title		Floppy
# hide (hd0,0)
# unhide (hd0,2)
# root		(fd0)
# chainloader	+1

title		MSDOS 6.22
hide 		(hd0,0)
unhide		(hd0,2)
root		(hd0,2)
chainloader	+1



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
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Tibor60 on 2006-02-18
I am afraid that with this automatic update my system is definitly trashed.
I have noticed that some services are not working, for example my Postscript Printer is stopped and no way to start again, it is impossible to use it. How to return to my previous system????

---

### Post by Tibor60 on 2006-02-18
Really no help? But if every automatic update can trash the system, than windows in reality much more safe. I can not print PDF for two days lready and a lot of problem, and nobvody can help...

---

