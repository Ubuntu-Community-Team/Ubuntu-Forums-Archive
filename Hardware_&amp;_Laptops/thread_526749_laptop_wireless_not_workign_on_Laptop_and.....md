---
title: "laptop wireless not workign on Laptop and...."
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by penguinux on 2007-08-15
hello!
I am trying to connect to the wireless network in my school but unfortunatly ubuntu does not detect it :(
I was wondering what I can do in order to make my wireless  work with my laptop "gateway"
OH! and one more thing, after installing ubuntu I no longer can boot windows vista :(
and now I can't use wireless network nor boot onto my windows vista os to connect to the wireless network.
It appears like I installed ubuntu on my first partition and it works very good, but there seems to be some problems with grub. I tried editing some lines so it can boot windows but it appears like my attempts were useless ;(
here is what my menu.lst file looks like 





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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

Windows Vista
title=Windows Vista
rootnoverify (hd0,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1


Windows Vista
title=Windows Vista2
rootnoverify (hd0,0)
map (hd0) (hd2)
map (hd0) (hd1)
chainloader +1

Windows Vista
title=Windows Vista3
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd0) (hd1)
chainloader +1


title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

title Windows Vista
root (hd0,2)
savedefault
makeactive
chainloader +1



### END DEBIAN AUTOMAGIC KERNELS LIST


i just tried to add several boot options for vista to see if they would work 
but none of them did. I think that the error was intalling ubuntu on my first partition
what I did was to format the recovery parition this laptop originally came with since I have a cd . 
help please!
i need this to work ....
thanks in advance!

---

### Post by fredj on 2007-08-15
You are now completely confused and none of those entries in menu.lst will work.
Your Linux is on (hd0,0) i.e. hardisk 0, partition 0
Your Vista is on (hd0,1) i.e. hardisk 0, partition 1.
Your entry for Vista should read something like

title        Microsoft Windows Vista
root       (hd0,1)
saveddefault
makeactive
chainloader +1

Get rid of all those confusing and confused disk mapping commands.

---

### Post by ugm6hr on 2007-08-16
Before doing anything else - boot Ubuntu and post the results from:
```
sudo fdisk -l /dev/sda
sudo fdisk -l /dev/hda

```

Then try and point us to which of the outputs is Vista partition.

And if you want to try and get wifi in Ubuntu - post the results from:
```
lspci -nn | grep Ethernet
lspci -nn | grep Network
lshw -C network
```

We'll try and help from there.

---

### Post by penguinux on 2007-08-17
well, thanks for the help guys,
but it seems like I solved my problem,
even though I had to start from scratch!!!
I figured out that my vista partition was probably damaged
when I resized it with gparted :(
Just decided to format everything out and start again, because
my partition were kind of messed up :S
Now I am dual booting vista and ubuntu :)
vista on my first partition and ubuntu on secound one.
it seems like I had ubuntu on first the first time and vista on the second one then unallocated partition at the very beginning of my hd.
It was the recovery partition my laptop came with :S
so i said **** this I am going to start from scratch, this is a complete mess
lol

---

