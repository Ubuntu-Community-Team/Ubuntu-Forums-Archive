---
title: "installing ubuntu on an old japanese mini-pc : Fujitsu FMV BIBLO loox S73A"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-07-06
hello all
i would love some pointers and ideas on how to install an ubuntu version on this old
 japanese mini-pc, a Fujitsu FMV BIBLO loox S73A.

the specs are low, and it doesn't have a CD drive, but two usb ports, wifi (no ethernet port)
i also have this usb to ethernet adapter for it.
using with windows xp in japanese is a pain, but otherwise it's a nice little machine that we would love to tug with us from next sunday onwards, on our travels, where we would use it for and internet browser, email, video and mp3, word processor and most of all emptying our camera's photos

i was think of installing a ubuntu distribution on a dedicated thumb drive or unpowered usb disk, which would ask disk space, and could be useful, but not sure if and how this is possible.

the device doesn't have a CD drive, though i could probably hook on up via usb.

here are the specs : 
 Fujitsu FMV BIBLO loox S73A
FMV transmeta Crusoe
Processor TM5800 726 MhZ
L1 cache 128kB
L2 cache 512 kb
240MB of RAM
7.99 GB of free disk on a 26.9 GB drive

thanks for your help !

all the best

ben

---

### Post by darolu on 2009-07-06
Ubuntu has an application to create booting USB Memory flash, all you need is the Ubuntu CD or .iso file, you can find the app under System - Admin

It will run slow on that computer though; so I **strongly** recommend getting Xubuntu instead.

I'm not entirely sure if the regular 32-bit version of Ubuntu will work on a TM5800 processor though, but based on this old thread it seems to work: [http://ubuntuforums.org/archive/index.php/t-993974.html](http://ubuntuforums.org/archive/index.php/t-993974.html)

By the way, I use this small distro for emergencies mostly, but it also works great with old computers, it fits in 50MB!: [http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

Let us know how it worked.

---

### Post by bjaz on 2009-07-06
finally decided to try and install it via a xubuntu live cd i have, yet the external USB CD drive i have doesn't seem to let me boot on it, with a xubuntu cd inside. 

any ideas on how to do this install without a cd drive ?

b

---

### Post by bjaz on 2009-07-06
> **darolu said:**
> Ubuntu has an application to create booting USB Memory flash, all you need is the Ubuntu CD or .iso file, you can find the app under System - Admin

It will run slow on that computer though; so I **strongly** recommend getting Xubuntu instead.

I'm not entirely sure if the regular 32-bit version of Ubuntu will work on a TM5800 processor though, but based on this old thread it seems to work: [http://ubuntuforums.org/archive/index.php/t-993974.html](http://ubuntuforums.org/archive/index.php/t-993974.html)

By the way, I use this small distro for emergencies mostly, but it also works great with old computers, it fits in 50MB!: [http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

Let us know how it worked.

thanks. i will focus on installing xubuntu from the usb drive.
darn small linux sounds good as well, but for the time being i'd rather try to install xubuntu on the computer, eventually getting rid of the japanese windows xp, and looking into ram expansion if it's available

how do i know if the bios supports USB booting ? i made a bootable usb drive as described here [http://www.pendrivelinux.com/usb-xubuntu-810-install-via-the-usb-creator/](http://www.pendrivelinux.com/usb-xubuntu-810-install-via-the-usb-creator/) but can't seem to be able too boot from it on the computer as well. boot device priority options are usb cd rom drive, hard disk drive and floppy disk drive...

seems like i'm stuck. can't boot /install from a usb cd drive (not recognized), USB drive was recognized in the japanese windows, but not since it was made bootable via USB Creator. and not when booting.

the bios is PhoenixBIOS 4.0 Release 6.0

i wouldn't mind deleting everything on this computer if i was sure a linux distro such as xubuntu would work fine, but this isn't clear. and as of now i have no idea on how to install it, if the usb drive booting doesn't work, nor if the external cd drive i have isn't recognized.

i have a xubuntu box, a xbuntu hardy live CD, Gparted, and now this USB creator created bootable usb available

the drive is still recognized in the japanese windows os, but if i click on wubi.exe, i am simply asked to reboot with an install cd in the drive, which is inexistant.


b

---

### Post by bjaz on 2009-07-06
is there anyway i could connect the mini computer to the xubuntu box i have via USB (or via the usb ethernet adaptor) and then install xubuntu on the computer via the other one ?
or a way to enable usb drive booting ?
i'm trying to install the CD boot helper from the drive, see if this will help

edit- made a slight progress, the USB CD drive i have was finally recognized by windows. I'm trying to run the CD boot helper from there, and to boot and install xubuntu.
the japanese windows os is a little odd, in that / signs are replaced by ¥ and other fun surprises that i'd love to forget about

------nope, that didn't work, the CD boot helper stops due to an "invalid argument"

still very much stuck
the cd drive is recongnized in windows, but i can't seem to be able to boot from it even though i put "boot from external cd drive" as a first priority in the bio's boot options
thanks

ben

---

### Post by bjaz on 2009-07-06
i'm trying an "install inside windows", to see if this can get me anwhere
but with a 239mb of RAM, i was warned that it might not work

---

### Post by ecmatter on 2009-07-06
Are you using the regular xubuntu live cd or the xubuntu 'alternate installation' live cd?  I had all sorts of problems installing with the live cd on an older machine.  The alternate installation cd worked.

Your mileage may vary, but I found xubuntu to be too much for my 1 GHz PIII with 256 Mb RAM.  Very, very slow.  Lots of lag.  If you're not going to (or not able to) add some RAM, you might want to look into some of the smaller distros like puppy or dsl.

---

### Post by bjaz on 2009-07-06
i'm trying with the regular xubuntu.
but so far i'm not really getting anywhere for the reasons explained above (booting issue)


i'd love to try DSL, but how ? 
usb booting or actual external CD drive booting doesn't work, so i'm not sure how to install it if i can't boot via usb or a cd drive
i just performed a test and apparently it's not possible to boot from an external cd drive or from a USB device.
the ram extension would be great, but i'm not sure the type of RAM used is easily found

i would need to instal DSL from inside windows, somehow, but i'm not quite sure how this is possible.

the standard xbubuntu works, but its in japanese though i had specified english (!), and it's hard to change it without setting up an internet connection.
it's also veeeery slow. i'm burning an alternate i386 xubuntu live cd and trying to re-install "inside windows" since i can't find any other way to install xubuntu without booting from a CD or USB drive


thanks

b

---

### Post by ecmatter on 2009-07-06
When you said you were &quot;intalling inside windows&quot;, I thought that meant you were using an installer like unetbootin rather than wubi.

Try this:  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

> 
[B]
[/B]UNetbootin can create a bootable Live USB drive, or it can make a "frugal install" on your local hard disk if you don't have a USB drive. It can load distributions by automatically downloading their ISO (CD image) files, or by using existing ISO files, floppy/hard disk images, or kernel/initrd files, for [installing other distributions]("http://unetbootin.sourceforge.net/#other"). 


I've never used it, but it sounds like it might be what you're after (provided you have an internet connection).  Unfortunately, it doesn't look like there's any built in support for xubuntu, but there are plenty of other lightweight distros to choose from. 

Last I checked, DSL was no longer being developed (infighting among the developers), so you might want to look into all of that before installing.  I've got nothing but good things to say about puppy.  Solid, fast, packed with programs, and under 100 Mb.

---

### Post by snowpine on 2009-07-06
If you have a working Windows install already, then Unetbootin is definitely the way to go. It supports all Linux distros that are distributed as an .iso file (including Xubuntu). Good luck!

---

### Post by bjaz on 2009-07-07
thanks for the tip, and sorry for the confusion, it was a WUBI install that i was refering to.
i downloaded unetbootin, and it does indeed support xubuntu and DSL.

things have evolved, since i can now boot to a xubuntu partition thanks to the WUBI install, yet the xubuntu is very slow.
i'm looking into puppy and dsl

yet this means i have access to a terminal and other things.
i also downloaded the unetbootin linux version

b

---

### Post by bjaz on 2009-07-07
ok, big improvement. I finally installed puppylinux on the hard drive, and it's really fast.
everything seems to be working fine, except the wireless configuration, since my network is hidden, ie won't show up in a scan, and there's no hidden option in clear view.

since i now have the unetbootin, i was wondering if the alternative xubuntu version might work faster, or is it not that different ? the speed difference i have between the standard xubuntu and puppylinux is pretty amazing, but i'm used to xubuntu, (which also made the wireless work straight out of the box whereas i'm struggling with puppy)
thanks

b

---

### Post by ecmatter on 2009-07-07
Glad to hear that unetbootin worked for you.

I couldn't get the regular xubuntu live cd to work on my machine, so I have no way to compare performance between the regular install and the alternative install.  The alternate install version lagged quite a bit until I added another 256 Mb RAM.  Now the speed is acceptable.

Booting via wubi will make xubuntu run extra slow (running two OS's at the same time), so you should see a lot of improvement were you to install via unetbootin.  It won't be as fast as puppy, but it should be a lot faster than what you're seeing now.

---

### Post by grndplane on 2009-07-07
I did this with an old hp laptop with no cd drive. I pulled the harddrive out and took it over to another computer. I did my installation, updated my programs and went thru the reboot process a couple of times. Then I put the harddrive back into the laptop. The first time it booted it went thru detecting new hardware and configuration then all was good after that. Hope this helps.

---

### Post by bjaz on 2009-07-09
> **ecmatter said:**
> Glad to hear that unetbootin worked for you.

I couldn't get the regular xubuntu live cd to work on my machine, so I have no way to compare performance between the regular install and the alternative install.  The alternate install version lagged quite a bit until I added another 256 Mb RAM.  Now the speed is acceptable.

Booting via wubi will make xubuntu run extra slow (running two OS's at the same time), so you should see a lot of improvement were you to install via unetbootin.  It won't be as fast as puppy, but it should be a lot faster than what you're seeing now.


thanks

it seems unetbootin seems to only allow one distro to be loaded, since it asks to be removed when i try to run it again. I also didn't see the alternative xubuntu distro offered for download in the unetbootin menu, so i think i'll stick with puppy for now (i'm leaving in three days, taking the mini computer with me)

---

### Post by snowpine on 2009-07-09
> **bjaz said:**
> thanks

it seems unetbootin seems to only allow one distro to be loaded, since it asks to be removed when i try to run it again. I also didn't see the alternative xubuntu distro offered for download in the unetbootin menu, so i think i'll stick with puppy for now (i'm leaving in three days, taking the mini computer with me)

You can download the Alternate iso of Xubuntu here: [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/xubuntu-9.04-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/xubuntu-9.04-alternate-i386.iso)

---

