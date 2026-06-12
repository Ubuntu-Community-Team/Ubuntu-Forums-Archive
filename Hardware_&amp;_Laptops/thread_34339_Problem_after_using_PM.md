---
title: "Problem after using PM"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by geearf on 2005-05-14
Hello,
i wanted to have some more partitions so i changed my /home et /swap from primary partitions to logical with Partition Magic, creating another one the be the one in primary mode.

But now when i want to boot in Ubuntu i get this :
"attempt to access beyond end of device
hde3: rw=16 want=8n limit=2
Kernel Panic - not syncing: I/O error reading memory image."

I've boot with the live cd, and found out that PM changed the hdex number, i changed them back in fstab, but i guess i need something better, cause still same problem :(

Thanks for the help,

edit : hde3 is the partition created to be the primary one, before it was /swap.

---

### Post by nad on 2005-05-14
You need to tell your bootloader, grub, where to find your init images.

Edit the file /boot/grub/menu.lst to point to your moved /boot partition/directory.

Perhaps:  # groot=(hd4,2)  to point to the third partition on your fifth ide device.

---

### Post by geearf on 2005-05-14
Hello,
i tried to reinstall the grub as said there : [http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows](http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows)

But same thing :(
As i've saw the / partition did not move.

Thanks for the help,

---

### Post by nad on 2005-05-14
Using the live cd, enter a terminal session and then the grub shell (type grub at the command prompt). Issue the command: find /boot/grub/stage1  note the location and type quit to exit.

If your / partition is /dev/hde3 and you let me know where the stage1 loader is, I will try to give you the command to repair grub.

---

### Post by geearf on 2005-05-14
i tried it, and it did not found anything :(

---

### Post by nad on 2005-05-14
Using the live cd, find your /boot partition/directory and post your file: /boot/grub/menu.lst .

From what I've read, you appear to have lost your /boot partition/directory.

---

### Post by geearf on 2005-05-14
Hello this is my menu.lst : 

And i can see my /boot in my / (hde2).
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
timeout         10

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
# kopt=root=/dev/hde2 ro

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

title           Debian GNU/Linux, kernel 2.6.10-5-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hde2 ro
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Debian GNU/Linux, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hde2 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Debian GNU/Linux, kernel memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title           Microsoft Windows XP Professionnel
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by nad on 2005-05-14
Going back to post# 2,

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

Your # groot=(hd0,1)  line should be: # groot=(hd4,1)

---

### Post by geearf on 2005-05-14
Hello i tried that, and i got exactly the same error.
Shall i change this : :"root (hd0,1)" also ?

Thanks

---

### Post by nad on 2005-05-14
My error. Yes, you need to change all those (hd0,1) lines to (hd4,1).

Don't forget to edit /etc/fstab also to reflect your / file system, /dev/hde2 .

And for (divinity of your choice) sake, don't forget to make a backup copy of your working menu.lst then run update-grub and make sure that everything still works.

---

### Post by geearf on 2005-05-14
Ok thanks, fstab already changed :)

---

### Post by geearf on 2005-05-14
grub told me it could not find hd4 :(

Thanks

---

### Post by nad on 2005-05-14
OK

Let's go back and list all of your drives, partitions and type of drives (ide,sata,raid,etc).

Something may be getting lost in our translation.

---

### Post by geearf on 2005-05-14
Sure,

and i wish to say i really appreciate all your help.
I have one hard driver, but it is not directly on the motherboard, it is on a UDMA100 controller on the motherboard (i think that explains the hde).
Then i have 1 partition for windows hde1, which is a primary one.
Then one partition for / hde2, which is also a primary one.
Then one primary partition, to be able to have logical partition (that's the one created today, and that made all things go bad) hde3.
Then one logical partition for /home hde6 and one logical partiton for /swap hde5.

I also have one dvd player, one dvd burner, and one cdwriter (this one is on the same controller the hard drive is) though i am not sure you wanted to know these too.
I also thought that hde would mean hd4, but it seems it does not, have no idea why.

Thanks.

If i cannot do anything maybe i should use PM again to go back to 4 primary partitions, and maybe i'l have the same numbers i used to have, and then i'll use QTparted to create others directly from linux ? (any comment on this would be appreciated too, as i plan to create a fat32 partition later on, and i do not want to go through this kind of trouble often, though once we find out how to manage with this one, the rest should be easy).

---

### Post by nad on 2005-05-14
Hmmm...

If (hd0,1) worked before and not now, it would seem that grub is having difficulty reading the new partition table on the offboard udma controlled drive. I suppose that the logical drives could be confusing it. It could also be a firmware issue with your controller and grub. You may wish to research bug issues with grub and your controller. I have had issues with promise controllers writing non-standard information to the partition table. The only way to correct it was to overwrite the entire mbr and reconfigure.

You may wish to backup your current mbr: dd bs=512 count=1 if=/dev/hde of=hde.mbr

and play with it, however, you are playing with fire. To restore the mbr to your file, reverse the input file (if=) and the output file (of=) in the command above.

You should also have a copy of your current partition table: parted /dev/hde print > hde.txt

If we all had this info, the Holy Grail of restoring, we would have more hair!

---

### Post by geearf on 2005-05-14
Hello, actually it is a promise controller i'm using.

But i feel like the grub is almost working.
Why ? because when i let the menu.lst like it was before, linux try to load (i see lot of stuff loading).
Then after loading the drives, it tries the partitions and that's when it fells i think, so i am not quite sur if it's only a grub problem.

Thanks

---

### Post by geearf on 2005-05-14
In fact,
i just tried booting memtest, and i can so i really doubt the grub is in fault (i may wrong though, that is why i am searching help :) )

---

### Post by geearf on 2005-05-14
well finally i reverted my partitions to how they were before, and now i am talking to you from my real ubuntu.
I'll try to find out how to setup another fat32 partition now without breaking all the rest...

Thanks,

---

### Post by nad on 2005-05-14
Your welcome. I wonder if pm had anything to do with it. If you ever find out what the problem was, post back.

---

### Post by geearf on 2005-05-14
Well i just spent another hour trying to make any existing parition into a logical one, but i could not.
Every time i tried something (only one partition, all partitions, etc), linux would just never boot.

So if you know a way for me to have a 5th partition, i'd be very pleased to know.
For now i am going to sleep :)

Also, once i had all my partitions in primary mode, but not in the right order, you know exactly what happened : another kernel-panic error, so i had to try to get them back in the right order, thank god explore2fs exists, cause thanks to him i did not have to reboot to look at my partitions from ubuntu live.

Thanks,

---

### Post by nad on 2005-05-14
Get another hard drive and put it on your second ide channel.

Just be ready to remap the drives again, although it is possible that it will use an unused /dev name.

---

### Post by geearf on 2005-05-15
Well for the moment i am not going for another hard drive :(
I just need a new partition :(

---

### Post by geearf on 2005-05-15
up for an idea on this anyone ? ;)

---

### Post by geearf on 2005-05-16
up ;)

---

### Post by geearf on 2005-05-20
Hello,

just to tell you that i managed to get that partition, i don't really know why cause for me i tried it the same way as last week end but now it works ..

In the meantime i only did change the kernel (386 -> k7).

Thanks anyway :)

---

