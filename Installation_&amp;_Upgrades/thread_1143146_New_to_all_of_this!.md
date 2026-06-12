---
title: "New to all of this!"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by dakota_oneill on 2009-04-29
Okay so this is my first time ever using Ubuntu etc. But I have a problem. I want to install Ubuntu, but not on my laptops only hard drive, I want to install it onto my external hard drive. Can I do that? And if I can, my external hard drive is 120 GB and has information on it, but can't transfer it anywhere since my laptop's hard drive is full. So can I install Ubuntu just right onto that with out lossing any data, or do I have to partition it, and if so will I lose my current data on it. Also if I figure all of this out, can I install Kubuntu onto the same external hard drive, so when I turn on my Windows Vista laptop I get that boot screan that would say Boot To Vista, Ubuntu, or Kubuntu??

Thanks a lot and sorry for the total noob question!

---

### Post by dakota_oneill on 2009-04-29
Also, I want the newest version, 9.04 Jaunty*

---

### Post by oldos2er on 2009-04-29
How much free space is on the external drive?

---

### Post by dakota_oneill on 2009-04-29
Uh 75 - 120 GB

---

### Post by MontelEdwards on 2009-04-29
> **dakota_oneill said:**
> Uh 75 - 120 GB
Of course you can do this. Just run the Live CD and then when in the installation manager, use the manual partition editor and find the external drive, format it, and then select is /

---

### Post by dakota_oneill on 2009-04-29
Thanks but I have tried downloading and burning the CD, but it doesn't work. Before my Vista boot screen I click F12 to get into the boot options then click DVD and it just boots Vista?

---

### Post by MontelEdwards on 2009-04-29
Umm, strange. are you SURE that it was burned?

---

### Post by dakota_oneill on 2009-04-29
Well I looked at the disk and clearly saw the difference, I used Roxio to do it, but have never used it before so I am not sure?!?

---

### Post by MontelEdwards on 2009-04-29
> **dakota_oneill said:**
> Well I looked at the disk and clearly saw the difference, I used Roxio to do it, but have never used it before so I am not sure?!?
I have used Roxio before when I ****** up Ubuntu and has to use my sisters computer. Just reburn the CD, and what computer do you have?

---

### Post by dakota_oneill on 2009-04-29
a dell inpiron 1525 laptop, with vista. and I have burned the cd onto dvd twice now!

---

### Post by upchucky on 2009-04-29
after ensuring that the bios is indeed allowing a cd/dvd boot first, check to see if the version u downloaded is a dvd version? if true, then is the laptop drive a dvd drive or just a cd? if only a cd then you need to use the cd version.

you can also remove the hard drive and then try to boot the cd/dvd
if still no joy, download knoppix live cd or dvd, depending on your drive.

knoppix will boot if the hardware is fine.

---

### Post by MontelEdwards on 2009-04-29
> **upchucky said:**
> after ensuring that the bios is indeed allowing a cd/dvd boot first, check to see if the version u downloaded is a dvd version? if true, then is the laptop drive a dvd drive or just a cd? if only a cd then you need to use the cd version.

you can also remove the hard drive and then try to boot the cd/dvd
if still no joy, download knoppix live cd or dvd, depending on your drive.

knoppix will boot if the hardware is fine.
Yeah, if it is a CD version use a CD...
Also, i believe that the laptop you're using is 64 bit so use the AMD64 download

---

### Post by lisati on 2009-04-29
Using the 64-bit version on a 64-bit machine is optional - the 32-bit version should work too.

Some tips on burning CDs & DVDs can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by MontelEdwards on 2009-04-29
> **lisati said:**
> Using the 64-bit version on a 64-bit machine is optional - the 32-bit version should work too.

Some tips on burning CDs & DVDs can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Well i know that...
But wont 64 bit OS run best on  a 64 bit processor?
and i think there is more software available that is 64bit

---

### Post by dakota_oneill on 2009-04-29
Kay, I'm dumb in this subject but not others, If I have vista I obviously have a DVD drive. Intel, Core 2 Duo, 32 Bit.

---

### Post by upchucky on 2009-04-29
hmm i shoulda seen that in my crystal ball.... I have had people bring me custom built pc and laptops with old hardware, there are a lot of shrewd sales people out there.

good luck

---

### Post by MontelEdwards on 2009-04-29
> **dakota_oneill said:**
> Kay, I'm dumb in this subject but not others, If I have vista I obviously have a DVD drive. Intel, Core 2 Duo, 32 Bit.
Oh ok. My sister has that same model and she is 64 bit. that is whyi said that

---

### Post by dakota_oneill on 2009-04-29
Kay well, I tried 5 other ISO burning things onto 5 brand new DVD's, and I restarted my computer for all of them clicked F12 to get into the boot manager thing, scrolled down and click Cd, dvd, drive etc DVD spun, and then just boot vista? This is making me not even want to try out Ubuntu and Kubuntu!

---

### Post by MontelEdwards on 2009-04-29
Ok i understand your frustration but just bare with us.
Why are you installing Ubuntu on a DVD? Just because you have a DVD drive dosent mean that you can use Cd's just use a CD. And if none works install it from USB [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by dakota_oneill on 2009-04-29
I'm using DVD's because all I have are DVD's they should still work, they are the same as CD's just bigger. And that link you gave me is options in Ubuntu, I don't have Ubuntu yet so I can't do that !?!? Lol.

---

### Post by MontelEdwards on 2009-04-29
> **dakota_oneill said:**
> I'm using DVD's because all I have are DVD's they should still work, they are the same as CD's just bigger. And that link you gave me is options in Ubuntu, I don't have Ubuntu yet so I can't do that !?!? Lol.
Yes but there is a program called Unetbootin which it gives instructions on which is available on Windows and Linux. I think that you will also get better help if you post this in absolute beginner because that is were the smarted people are.

---

### Post by upchucky on 2009-04-29
did you remove the hard drive?
did you actually go into the bios and not the quick boot option? and make sure the cd/dvd boot is enabled some bios disable the feature as a security option.

one of my laptops has the f12 quick boot option, but also has f2 to actually enter the bios to enable/disable options.

---

### Post by dakota_oneill on 2009-04-29
> **upchucky said:**
> did you remove the hard drive?
did you actually go into the bios and not the quick boot option? and make sure the cd/dvd boot is enabled some bios disable the feature as a security option.

one of my laptops has the f12 quick boot option, but also has f2 to actually enter the bios to enable/disable options.

Okay I didn't change the boot order, I know how to do that, but if I change it to DVD first and it doesn't work will I still be able to get back into vista and or change it back to normal (e.g the laptops hard drive) And I can't remove my hard drive, my warrenty seal is right there which is just dumb.

---

### Post by upchucky on 2009-04-29
yes u can change it back, but it has to be done in the bios. and you do not need a hard drive in a machine to get warranty, in fact i removed my hard drive when i sent my laptop to dell and they had to warranty replace my screen.

but then i am the kinda guy that wins those kind of arguments with stoopit sales people, i have qualifications coming out the wazoo.

---

### Post by dakota_oneill on 2009-04-29
Okay I changed the boot order and a brand new ISO DVD and still nothing, it sayed it there was no bootable drive.

---

### Post by upchucky on 2009-04-29
it said there was no bootable drive, or no bootable media in the drive, if no bootable drive, then this is sounding more and more like a flaky cd/dvd drive.

what happens when you put in the windows recovery disk? does it boot?

to verify the cd/dvd is ok try a known good music cd, and a known good dvd movie in windows, do they play fine?

if yes then i suggest trying the alternate cd of ubuntu, or knoppix

---

### Post by dakota_oneill on 2009-04-29
yes my drive works, I will torrent the alternate cd then. and then try it all again.

---

### Post by upchucky on 2009-04-29
just for information, Knoppix is not only a great Linux version,but its real merit is in it's administration and maintenance functions, i have used it to repair many windows systems that have been brought down by malware and user error.

Knoppix shines in its hardware recognition and troubleshooting capabilities on just about any hardware out there.

I am not suggesting to run and use Knoppix, only to take advantage of it's superior hardware detection abilities and use that info to find out why your drive is being stubborn.

however anyone that wants to play with Linux, Knoppix is a great toy and OS.

---

### Post by dakota_oneill on 2009-04-29
Okay, Okay, Okay, Okay, I finally got the Kubuntu CD to work, so I put it in, booted to it, and the set up was all in like a blue screen and I did it up until it said prepping to partition drives. Right away I pulled out the DVD and turned of my laptop, because I didn't know what drive it was doing it to, or what so what do I do. I want to have it put on my external hard drive?

---

### Post by dakota_oneill on 2009-04-29
If I let it "prep" for partitioning would it have let me choose or what? I haven't backed up any of my laptops "main hard drive" stuff because I don't have another drive right now and can't risk losing it all!

---

### Post by oldsoundguy on 2009-04-29
did you burn the cd as an iso or just copy the download to a disk?  (ISO is the way to do it.)

---

### Post by dakota_oneill on 2009-04-29
Iso

---

### Post by dakota_oneill on 2009-04-30
Okay, Okay, Okay, Okay, I finally got the Kubuntu CD to work, so I put it in, booted to it, and the set up was all in like a blue screen and I did it up until it said prepping to partition drives. Right away I pulled out the DVD and turned of my laptop, because I didn't know what drive it was doing it to, or what so what do I do. I want to have it put on my external hard drive?
If I let it "prep" for partitioning would it have let me choose or what? I haven't backed up any of my laptops "main hard drive" stuff because I don't have another drive right now and can't risk losing it all!

---

### Post by upchucky on 2009-04-30
yes it would have let u choose, more importantly, did the live cd boot to a graphical display before actually telling it to install?

this is the try before installing option, and should be done to prove your hardware is ok with ubuntu.

since you have an external drive why not back up stuff to it? there should be room on that drive for your back up and ubuntu.

to be safe, there is a free windows program called ntfsclone.

this program lets you create an image of your functioning windows install, complete with all your files and programs, you create the image then store it on the external drive. or dvd, or usb thumbdrive, or network drive.

if you damage windows, or malware strikes, or windows slowly self destructs as it is programmed to do, it is a simple 20 minute procedure to restore windows complete with all programs, settings, and files.

if you have set up windows to have a separate partition for your files, you can also image it too.

when you want to do the actual install select manual, and tell it to set up on the external drive, this will also require customizing of the grub bootloader after the install completes, and you are gonna need to get supergrub to set up grub.

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the  grub instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

it is much simpler to do a dual boot install on the existing drive,

now be warned that when you do the actual install, it may seem that windows has gone, and/or ubuntu is also gone, this is not true, it just needs to be set up to be bootable in grub. do not panic. there is also a possibility that some settings for the display will need to be done, but one step at a time.

this is my grub/menu.lst file that allows me to boot winxp and ubuntu, it will be different than yours but it give you the general idea of what to look for if you have booting issues. not every machine does, but some do not boot right away. usually it is simply because of the wrong or missing entries in the menu.lst file.
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
# kopt=root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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



title		Ubuntu 8.04, kernel 2.6.24-16-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.24-16-386


title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

 
```

---

### Post by dakota_oneill on 2009-04-30
> **upchucky said:**
> yes it would have let u choose, more importantly, did the live cd boot to a graphical display before actually telling it to install?

this is the try before installing option, and should be done to prove your hardware is ok with ubuntu.

since you have an external drive why not back up stuff to it? there should be room on that drive for your back up and ubuntu.

to be safe, there is a free windows program called ntfsclone.

this program lets you create an image of your functioning windows install, complete with all your files and programs, you create the image then store it on the external drive. or dvd, or usb thumbdrive, or network drive.

if you damage windows, or malware strikes, or windows slowly self destructs as it is programmed to do, it is a simple 20 minute procedure to restore windows complete with all programs, settings, and files.

if you have set up windows to have a separate partition for your files, you can also image it too.

when you want to do the actual install select manual, and tell it to set up on the external drive, this will also require customizing of the grub bootloader after the install completes, and you are gonna need to get supergrub to set up grub.

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the  grub instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

it is much simpler to do a dual boot install on the existing drive,

now be warned that when you do the actual install, it may seem that windows has gone, and/or ubuntu is also gone, this is not true, it just needs to be set up to be bootable in grub. do not panic. there is also a possibility that some settings for the display will need to be done, but one step at a time.

this is my grub/menu.lst file that allows me to boot winxp and ubuntu, it will be different than yours but it give you the general idea of what to look for if you have booting issues. not every machine does, but some do not boot right away. usually it is simply because of the wrong or missing entries in the menu.lst file.
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
# kopt=root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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



title        Ubuntu 8.04, kernel 2.6.24-16-386
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-386
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd        /boot/initrd.img-2.6.24-16-386


title        Ubuntu 8.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

 
```

Okay lol, you lost me. (did the live cd boot to a graphical display before actually telling it to install?) no it was a blue screen with white text. But like I said (it is much simpler to do a dual boot install on the existing drive,) I don't want to do that, like I said I want to have it on my external hard drive!

---

### Post by upchucky on 2009-04-30
k the most important part of my post is about using supergrub to set up the grub bootloader to boot the external drive. you may not need it, it may just as well set up first try.

since you want to have it on the separate drive then it is simple enough to use your f12 to select which drive to boot, making sure they are both enabled in the bios as selectable by means of the f12 key.

when booting with the ubuntu disk, select manual install, then select the usb external drive, hopefully it all goes automatic from that point.
good luck.

---

### Post by Rick_911 on 2009-04-30
I had a similar problem and I had to go into the bios and reset the vista machine to boot from cd/dvd first

Prior to doing that nothing would work. It behaved as if it were a blank disc.

---

### Post by razy60 on 2009-04-30
AS has been previously mentioned you should try unetbootin.
[HTML]http://unetbootin.sourceforge.net/[/HTML]
all you need to do is download the installer program (in windows is best), plug in your external drive and load the OS of your choice to the location of your choice, the benefit of this is that you have a fully portable system and it is designed to load straight on to an external USB device,to use it just plug it in and restart choose boot from USB and your good to go.
i have a 2GB stick with pclinuxos and 8.10 on which works fine.

Raz

---

### Post by dakota_oneill on 2009-05-01
Okay I finally got Kubuntu installed. But now I have a problem, because I didn't know what I was doing it partitioned my hard drive, into three drives. So my 120GB external hard drive is now

[IMG]http://sixpop.com/files/152/errr.jpg[/IMG]


[IMG]http://sixpop.com/files/152/errr1.jpg[/IMG]

I thought i when I set that number to 40.5 was going to be the install not the only room I have. So my 38.2 GB of stuff on my hard drive is there and I can't have anything else! And as you see in the first image there is a second partition on it that is 68.30 GB but I can not access that. So how can I fix it so I have as much room in my "F" drive as possible which I think (it said when I was setting the numbers) 110 GB?

---

