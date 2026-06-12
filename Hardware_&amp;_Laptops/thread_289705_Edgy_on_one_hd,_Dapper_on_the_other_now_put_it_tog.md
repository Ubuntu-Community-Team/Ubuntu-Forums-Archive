---
title: "Edgy on one hd, Dapper on the other: now put it together."
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by BLTicklemonster on 2006-10-31
Okay, here's where I am right now:

My computer has been normally running two hard drives, dual booting, one with two partitions, XP (fat32) and Dapper, the other hd for storage (fat32), and I have a dvd and a dvdrw.

The two HDs on ide one, dvd and dvdrw on ide two.

I had a spare hard drive, and wanted to try out Edgy, so I pulled the two HDs off of ide one, and put the spare there, and spent the weekend playing around with Edgy, and now have it where I want it. 

So as it stands, while using Edgy, I have my original two hard drives sitting off to the side unused, and when using Dapper, of course, I have the Edgy hd sitting off to the side.

What I'd like to do is the obvious: win the lottery and marry Heather Locklear. But that's not about to happen, so I'll settle for being able to tie all 3 hard drives in together at the same time, with Edgy being the number one listed in grub.

I would imagine that there are several ways to go about this. I have a Maxtor Ultra 133 pci mass storage card, so I suppose I could hook that bad boy up and and just plug in the other drive (I am thinking this is the undesirable option), or I could remove the dvd (leaving the dvdrw of course) and just put the Edgy hd in it's place and edit grub to reflect this new set up. (which, imho, is the desirable option, though I like having both drives).

Now come the requests for tech advice...

First, will the ata 133 card work in ubuntu, and how do I get the drivers (you don't have to hold my hand on this one, just yes or no) if I decide to go that route, though I seriously doubt that I will.

Second, I assume that the ideal thing to do is to drop the dvd and put the edgy hd there, then edit grub to show the edgy information in the old dvd space, right? Which grub would I edit then; the one on edgy or the one on dapper, or both? Could it really be that simple? 

Why would I be doing this? For several reasons, the most obvious being that I never do things that make sense, and also because the Dapper has stuff I want like pictures and links, and stuff. I will probably be dropping xp altogether soon anyway, and once I get all my dapper stuff (and whatnots from the xp drive), I can remove that drive and go back to two hds on ide 1, and a dvd and dvdrw on ide2.

And no, dist upgrade on dapper is not an option, so don't go there.

---

### Post by TLE on 2006-10-31
> **BLTicklemonster said:**
> First, will the ata 133 card work in ubuntu, and how do I get the drivers (you don't have to hold my hand on this one, just yes or no) if I decide to go that route, though I seriously doubt that I will. I'm pretty sure that wont be a problem, it should work out of the box but I'm not 100% sure on that one, maybe like 98%.

> **BLTicklemonster said:**
> Second, I assume that the ideal thing to do is to drop the dvd and put the edgy hd there, then edit grub to show the edgy information in the old dvd space, right? Which grub would I edit then; the one on edgy or the one on dapper, or both? Could it really be that simple?
I would seriously recommend putting the dapper disks back the way they used to be and then putting the edgy disk in one of the dvd drive slots.
The reason for doing that is that, in the Dapper setup we have two OS' working the way they should, and we have win back as the first partition where it wants to be.
So when you have that setup, the mbr will load the grub that is on you dapper setup so that is the one we want to edit. But first make sure that you have your edgy partitione mounted in dapper so we can just copy the entries from the edgy/grub/menu.lst.
So if all that is good, we are at the point now where we are going to edit the /boot/grub/menu.lst on the dapper system (remember to make a safety copy). Here you should notice that there is a section of that file that is being edited by apt when it install new kernels, DO NOT CHANGE ANYTHING in between those two markers. Then copy the boot entries from the edgy menu.lst down BELOW that section that we don't want to edit and change the partitionname appropriately. That actually means that edgy will not be the first entry in the grub as you asked but it doesn't matter because you can still make it the default. Just count what number entry it is and find the place in the menu.lst where it says default something, uncomment it and change the number appropriately. That's it. Then when dapper gets a new kernel it will happen automatically and the only thing you have to do is to change the deafult number,and when edgy gets a new kernel you will have to copy over the new entries and change the default number.
Regards TLE

PS: Just write me if you need a more thourough explanation of the menu.lst stuff, I just didn't know how much to include

---

### Post by BLTicklemonster on 2006-10-31
Pretty straightforward, thanks a million. I'll give it a go later on today and see how totally messed up I can make things before pleading for help! 

I agree with you on how to go about with the drives and all for sure. I'll save my sources from edgy and email them to myself before making the plunge. So can I use [diskmounter](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d) in dapper to mount the edgy disk? Or just use the information from the sources in my dapper sources, then reboot, then mount? Not really certain ... no wait, I'll have to do that in edgy later. 

I'll holler once I get edgy in. :)

---

### Post by BLTicklemonster on 2006-10-31
Alllllrighty then...


having no idea whatsoever what I was doing, I proceeded to take the grub and fstab info and email it to myself, then in dapper, I edited them, adding this to the end of my fstab:

```
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c /               reiserfs notail          0       1
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a none            swap    sw              0       0
```

Of course that would not work, because the hdb2 part would not be right in dapper, so not knowing how to mount the partition, but knowing that I can find out the hd stuff in system>administration>disks, I went there, found my drive and learned that in dapper, though unmounted and all, it listed them as 

hdd1 and hdd2 with swap as hdd2, therefore, I changed it to this:

```
# /dev/hdd1      /               reiserfs notail          0       1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c /               reiserfs notail          0       1
# /dev/hdd2            none            swap    sw              0       0
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a none            swap    sw              0       0
```

notice I even moved the mount stuff and all up so the uncommented lines looked right and all.


But it won't boot. I can't remember offhand what I put in the grub as far as 

```
root		(hd0,0)
``` for the edgy is, and I bet that is the problem.

If I try to boot to dapper normally, it says a partition isn't right. If I boot to recovery and try to edit fstab and comment out the edgy hard drive stuff, guess what? I can't save, because I have a read only file system of all things.

So now, I need to know how to get this figured out.

I could just put a live cd in, and reinstall edgy, but would the incorrect fstab and grub stuff from the dapper drive have an effect on anything? 

I'd rather not do that if I can force Dapper to behave, but if that is what has to be done, then that is what has to be done.

So is there any way to make dapper allow me to write to it?

Thanks.

---

### Post by BLTicklemonster on 2006-10-31
Okay, I took care of that with the live cd, now I have booted to dapper, and I created a directory /media/hdd1, and went to disks and set that as the access path, and can now browse contents of that drive. But it's showing this in grub:

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot
```

No way, that's not right at all, is it?

hd0,0 is the first partition of my master, which is where windows is, and hdb1 can't be right either.

Now what?


*edit:

Okay, I got it now. 

I have 3 hard drives, and I know that in order, the edgy would be the third one, therefore
root		(hd2,0)

and hdd1 and viola, I'm able to boot to edgy now.

Thanks for the help. Now to get with you on msn about that default boot part.

---

### Post by TLE on 2006-10-31
I'm assuming that is the edgy grub config. No that's not right because that was what they were named when edgy was on the first disk which was the only one that was in. The thing is that there is like three different ways of naming partitions so that can be a bit confusing, Try to give me the output from
```
df -h
```
in Dapper.
[EDIT]
Damn you're fast. Ok I've added you in msn so I think you have to approve me. Bu otherwise we can do it here. Please paste your entire menu.lst and I'll explain from that.

---

### Post by BLTicklemonster on 2006-10-31
*EDIT: MY BAD, THAT WAS THE WRONG ONE, HERE'S THE RIGHT ONE FROM THE DAPPER DRIVE.

Here you go, thanks. Time to go trick or treating with the kids. 

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu, kernel 2.6.17-10-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



```

Now which part of that gets moved to make edgy the default? Will that mean that it will say I have so many seconds to press esc to reach the boot menu before it boots?

*EDIT:
I found this:
```

 How to change default Operating System boot-up for GRUB menu

    * Read #General Notes 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

    * Find this line 

...
default     0
...

    * Replace with the following line 

default     X_sequence

    * Save the edited file 
```

and I see default as being 0 meaning the first os in the list, which is Dapper. The second os in the list is Edgy, the third is XP. Therefore, I would imagine that if I were to want to boot to say windows, I would have default set to 2; for Edgy, it would be 1. 

Now to get it to boot with the menu hidden for 3 seconds so that I have to press esc to see grub, I change

#hiddenmenu
to
hiddenmenu

and the timeout from 10 to 3, I hope. :)


*EDIT AGAIN LOL
Okay, so in menu.lst, any uncommented line is an option, so I finally counted down and got the right one booting so I boot straight to Edgy now!

but there's this here problem... Dapper, hda3, is now read only. I can liveboot and edit the menu.lst to get it to boot to edgy, but what if I want to boot to dapper now? And hda3 doesn't show up in Edgy at all. I am used to using system>administration>disks to see my drives, but I don't see that now in Edgy. Is there a program for doing that in Edgy? I can navigate to /dev and see hda2, but there's a red block with a white x on it. I know the system knows that it's there, but I'm at a loss here to get that particular drive to load up. Should I edit fstab, I suppose, to this?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c /               reiserfs notail          0       1
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda5 /media/hda5 vfat rw,user,fmask=0111,dmask=0000 0 0
[COLOR="Red"]#and heeeeeres Dapper
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1[/COLOR]
```

Nope, can't have that / there. So I need to mount that to /media/hda3, but without disks, I'm afraid that my capabilities are limited. Searching the forums gives me an information overload for sure.

But I see this:

> Yes, that's right. Edgy has installed its own boot-menu and made the MBR (and bootloader) to boot by using it. Edgy is in charge.

You can give control back to Dapper quite easily. Do this

1) Boot up using the Dapper Live CD.
Edgy's or another Live CD will do as well.

[ You could easily boot into Edgy and do all the work from there, but it's better to use a LiveCD for disk maintenance tasks.]

2) You have booted into LiveCD.
Start terminal program (gnome-terminal) from Applications -> >Accessories menu and issue these commands:

BTW: You haven't told about the disks, so I assume here that
/dev/sda1 = Dapper Drake partition
/dev/sda2 = Edgy Eft partition

Mount Dapper's partition to /media
$ sudo mount /dev/sda1 /media

Make chroot jail on /media
$ sudo chroot /media

You should now see a root prompt (#).
Re-install grub on /dev/sda (Replace MBR on the MAIN boot disk.
That is the disk your PC's BIOS will boot from).
# grub-install /dev/sda

Alternative command: You can also achieve the same result witout using chroot jail. /media has to be mounted as explained.
$ sudo grub-install --root-directory=/media /dev/sda

(Of course, replace /dev/sda1 and /dev/sda with correct disk in your case)

3) Reboot
# reboot
---------------------------------

4) Take the latest copy of menu.lst

As you know, Edgy has the latest (newest) copy of /boot/grub/menu.lst.

You can replace Dapper's /boot/grub/menu.lst with Edgy's or just copy over the new menu-lines so you can dual-boot between Dapper and Edgy.

$ sudo gedit /boot/grub/menu.lst

// moma
[http://www.futuredesktop.net/ubuntu6.06.html](http://www.futuredesktop.net/ubuntu6.06.html)


ps. If you have further questions, copy and paste output of these commands w/ your message.

$ sudo fdisk -l

Take the essential lines only (no # comments)
$ cat /boot/grub/menu.lst

which I'll try this evening when I get home from work.

---

### Post by BLTicklemonster on 2006-11-02
I can't boot to dapper any more. it hangs on the splash screen. I can go to recovery, and type startx, and I get errors saying that the system 

cannot create temp file ~ read-only file system


Dapper fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  0  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#and heeeeeres Dapper
#/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  0  
/dev/hda3                                  /media/hda3     ext3         defaults                       0  1  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0  

```

Dapper menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4

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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

#title		Ubuntu, kernel 2.6.15-27-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-27-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-27-386
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu, kernel 2.6.17-10-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```


Edgy fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  1  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#and heeeeeres Dapper
#/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  1  
/dev/hda3                                  /media/hda3     ext3         defaults                       0  0  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0  

```

Edgy menu.lst

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
# kopt=root=UUID=a09e3c82-9a50-4582-abfc-4befba58f24c ro
# kopt_2_6=root=/dev/hdb1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

in case that is of any help.

---

### Post by TLE on 2006-11-02
It looks like the two fstabs are the same. Are you sure you posted the right one for Dapper ?

Anyway hold on, I'm busy all day today but will have a look at it friday afternoon (GMT+1)

Don't go doing anything radical. I'm sure we can fix this.

---

### Post by BLTicklemonster on 2006-11-02
After exhaustive research.... the most logical thing I saw was a post stating that while dual booting, if one had problems, one might do this. ( *edit: meaning put the same fstab on each hard drive) There is one slight difference between the two. The line for the default system ends with a 1, respectively. Thanks Kenneth.


(I can boot in recovery, so what if I did 

sudo chown username:username -R /home/username ? )

I wonder if can you do this

---------
df -h
---------

to dapper ( /dev/hda3 ) from within edgy? cd /media/hda3 then df -h maybe, or /dev/hda3... I'll play around with it tonight and see.

I'll have to play around and see, because I bet that information would be helpful to you.

---

### Post by TLE on 2006-11-02
I think I've got it. But ok first of all I'll try to clear up a few things. First of all, what is it we have done and how would it work when we get it to work. Don't know how much of this you know but I would just like to be sure. So this first part of the post has nothing to do with your particular problem but is general info.

The first section of whatever harddrive is set up to be the "read-on-bootup" one in your BIOS, is the Master Boot Record (MBR). This is the first place you computer will look for instructions on what to when you start up. So back when you had WinXP there was info on that it should start to read the partition where XP was on, then when you installed Dapper it replaced the info XP placed there with GRUB, GRUB is meant to let you boot many different system. Now GRUB is placed in the MBR but its config file isn't, so besides GRUB it also holds information on what partition the config file is on. And then it loads it. So when you installed Dapper it told GRUB that its config-file was on the same drive.

Then when you switched drives and installed edgy, the exact same thing happened there. So on the edgy disk is also a GRUB in the first section of that drive that says its config is in the appropriate partition there. Now THAT was the reason why I wanted to start with the Dapper discs in, because there most files was configured right. But remenber that this means that the menu.lst file in edgy NEVER gets read because the GRUB that wanted to read that is in the first section of a haddrive that is NOT the "read-on-boot-up"-drive anymore and so doesn't get read at startup.

Now in the menu.lst are some entries like this one:
```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot
```
There are one of these for each kernel (Don't know if you know about kernels but it is that absolute core of a GNU/Linux system like Ubuntu) there is installed and every way it can be booted. So in your edgy menu.lst we can see that edgy can be booted with two kernels 2.6.17-10-386 and 2.6.17-10-generic and each of these can be booted in normal or recovery mode. Now this is one of things you asked earlier, when you want to figure out which number to put in the default line, it is the number if these entries! NOT just the number of systems like Dapper or Edgy, so the combinations i mentioned above would give **4** entries. So from the menu.lst from Dapper you have pasted we can see that Edgy is entry number 4 and WinXP number 6. (Or 5 and 7 if the:
```
title		Other operating systems:
root
```
entry gets counted to, and maybe it zero based (I think it is) so it can also be 3 or 5...... oh but anyway I'm not much help there it would seem, but anyway you can experiment with that without any danger to anything I just wanted to clear up that it is the entries we count.)

Sooo anyway. Now that we actually have it booting the right system we can forget about GRUB and the menu.lst for a while. The fact that you drive is read only is not, to my knowledge anyway, a GRUB problem. GRUB only tells the computer where to start reading a system, it has nothing to do with mounting you partitions. Now I'm pretty sure that the problem is in the fstab so you should NOT try to manually fix with
```
sudo chown username:username -R /home/username
```
it wont help anyway. And on a little side note the:
```
df -h
```
was just a command I wanted you to execute to get a little overview of your partitions. What it shows is a list of the partitions and where they are mounted. But it shouldn't really be nescessary now since I think I know what the problem is. When I first saw your fstab I was really surprised to see those
```
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c
```
"things" in the middle of everything since I have never seen that before and I didn't think it was supposed to be there. So I searched a little around and found this thread:
[http://www.linuxin.dk/forum/index.php?ops=linuxin&fmode=vis&visid=24209&grid=2]("http://www.linuxin.dk/forum/index.php?ops=linuxin&fmode=vis&visid=24209&grid=2")
(It's in Danish so it probably wont be very interesting for you anyway *G*)
But, what it says is that you can probably fix it by removing that wierd looking "UUID=a09e3c82-9a50-4582-abfc-4befba58f24c" and just writing the partition designation instead.
So what I want you to try. (Please back up the fstab before modifying it so we have it later for reference, if it doesn't work) is this:
Boot up from a live cd so you can get write acces to your Dapper partition, then, in your fstab replace the UUID=.... thingy with the partition name written just above it after the # ,so that this part of your fstab
```
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  0  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
```
would get to look like this:
```
# /dev/hdb1
/dev/hdb1  /               reiserfs     notail                         0  0  
# /dev/hdb2
/dev/hdb2  none            swap         sw                             0  0  
```

Oh and yes that's right, you should probably change that last 0 to a 1, it's not important for this problem, the only thing it means is that the filesystem on that partition will be checked regularly by fsck (a file system checking utility) but 1 is the defaukt setting for the / partition. So all in all it should be:
```
# /dev/hdb1
/dev/hdb1  /               reiserfs     notail                         0  1  
# /dev/hdb2
/dev/hdb2  none            swap         sw                             0  0  
```
But try to change the other thing first so we don't do more than one thing at a time.

Hope this helps. Let me know how it goes.
Regards TLE

---

### Post by BLTicklemonster on 2006-11-02
Okay, I see what you're saying. That uui whatever stuff is in the edgy fstab only. Must be their new way of identifying stuff is all I could come up with.

I'm familiar with all you said, but thanks for taking the time to post it anyway. I mean someone who doesn't know might one day come by this thread and see something they need to know. (one thing I think most people don't get is the openness of these forums. Which is why imo everyone ought to post as much info as possible when replying to a thread. Sometimes I look for an answer, and I find two techies working over something that would help me, but the answer given is something along the lines of, "use garflab to bnibble the fnarknark". Sure, Beldar might get it, but it does the average new ubuntu user browsing the forums no good.)

I'll try that real quick and see what happens. BTW, I am in edgy with hda3 mounted, and have been editing grub and all from here, so no need as far as I can tell for using a live cd.

*edit:

Wait!

```
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  0
```

is edgy, and

```
/dev/hda3                                  /media/hda3     ext3         defaults                       0  1  
```

is dapper.

So why would I be editing the fstab stuff for edgy?

---

### Post by BLTicklemonster on 2006-11-02
Dapper has booted, and I'm posting from it now.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
/dev/hdb1                                 /               reiserfs     notail                         0  0  
/dev/hdb2                                 none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
[COLOR="Red"]#and heeeeeres Dapper
/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  1  
#/dev/hda3                                  /media/hda3     ext3         defaults                       0  0  [/COLOR]
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0
```

The change I think that did it though is in red. (yeah, I did two things at once, but what you see here is copied from an earlier post, my fstab had original lines commented out, and more comments as a guide added in case I had to edit it again)

it used to look like this:

```
/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  1  
#/dev/hda3                                  /media/hda3     ext3         defaults                       0  0  
```

I was about to save and boot, when I realized we were editing edgy, not dapper, then I noticed the errors-remount-ro section, and I looked back at the orginal fstab from when dapper was not changed at all, and it was there. So automounting hda3, though it did mount it for me, left that crucial remount section out, so I never could gain access to a mounted writable drive is what I am guessing was the problem. 

Anyway, I'm here in dapper posting. Of course I didn't need to boot to it, because I could access everything I needed from edgy because it was mounted, but I saw a challenge and it was eating me up that I could not boot to dapper.

Now somewhere along the chain of events, I did something wrong that made me go to all this trouble. I can't imagine what it was, but at least this is here documented in case anyone else stupids out and has the same problem.

I want to thank you for this great learning experience. I'd still be staring off into space if it weren't for you coming in and helping, Kenneth.

The neat thing about this is, edgy is mounted for me already, woot woot. lol

---

### Post by TLE on 2006-11-03
You're welcome.

BTW could you post both of your fstabs here so the thread has sort of the "solution"?

Have fun with Ubuntu
Regards TLE

---

### Post by BLTicklemonster on 2006-11-03
Here's dapper:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
/dev/hdb1                                 /               reiserfs     notail                         0  0  
/dev/hdb2                                 none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#and heeeeeres Dapper
/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  1  
#/dev/hda3                                  /media/hda3     ext3         defaults                       0  0  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0
```

and here's Edgy:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  1  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#and heeeeeres Dapper
#/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  1  
/dev/hda3                                  /media/hda3     ext3         defaults                       0  0  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0
```

Thanks again, and have a great weekend.

---

### Post by BLTicklemonster on 2006-11-09
Fresh install of edgy on hdd 2 ide2 slave with hdd1 on ide1 master, hdd2 on ide1 slave, yet the same problem exists. I can see hda3 (dapper) from edgy (it boots to edgy and xp fine, but dapper won't come up, same problem as before) so I haven't persued this, but it bothers me that it happened at all.

Here's Dapper's boot menu and fstab

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

#title		Ubuntu, kernel 2.6.15-27-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-27-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-27-386
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu, kernel 2.6.17-10-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

__________________________________________________


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  0  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
/dev/hda3                                  /media/hda3     ext3         defaults,errors=remount-ro     0  1  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         rw,user,fmask=0111,dmask=0000  0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0 

```

and here's edgy's boot menu and fstab 

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
color cyan/blue white/blue

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
# kopt=root=UUID=f83fafab-ed71-47a6-ba81-357f96181586 ro
# kopt_2_6=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-27-k7 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
#title		Windows NT/2000/XP (loader)
#root		(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1




____________________________________________________


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  1  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
/dev/hda3                                  /media/hda3     ext3         defaults,errors=remount-ro     0  0  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         rw,user,fmask=0111,dmask=0000  0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0 

```

Per Kenneth's request. :)

---

### Post by BLTicklemonster on 2006-11-09
Bingo:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  1  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
/dev/hda3                                  [COLOR="Red"]/media/hda3[/COLOR]     ext3         defaults,errors=remount-ro     0  0  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         rw,user,fmask=0111,dmask=0000  0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0
```

There's the problem. I changed it to / and it booted. Didn't you mention something about that earlier today, Kenneth? 

Now that I've taken time to actually look at it, it's staring me in the face. Thanks for your help!

---

