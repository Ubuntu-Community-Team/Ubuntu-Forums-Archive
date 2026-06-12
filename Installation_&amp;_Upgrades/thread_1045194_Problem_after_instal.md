---
title: "Problem after instal"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by NuttyMonk on 2009-01-20
Hi all,

i have just tried to do my first ever install of a linux OS so i'm a mega-noob with Ubuntu.

My PC is kinda old and crappy and wouldn't let me burn the install pachage to CD so i installed it using Daemon-Lite ISO mounting software in windows.  I installed it onto a clean, newly formatted hard disk.  When i reset the PC and chose the Ubuntu OS to load it did some more install stuff.  Now when i go through the boot up process and load Ubuntu as the OS it does all of the DOS-based text stuff and goes to the creamy coloured page where i put in my user and password.  After that nothing happens.  The screen just stays as it is.

I've been trying to find out what might be wrong in the documentation here on the Ubuntu site but i'm not getting anywhere. Could anyone offer me any help?  There were no error messages during the install.  I have onboard graphics and sound.  I obviosuly don't have a CD in the drive to do a CD-based boot since my pc couldn't burn to CD.  I did the MD5 checksum after downloading the install pack and it was OK.

Any help anyone has would be greatly appreciated.

Cheers

NM

---

### Post by overdrank on 2009-01-20
> **NuttyMonk said:**
>  Now when i go through the boot up process and load Ubuntu as the OS it does all of the DOS-based text stuff and goes to the creamy coloured page where i put in my user and password.  After that nothing happens.  The screen just stays as it is.

NM

Hi and welcome, could you give us some system specs as it sounds like it maybe a resource issue.

---

### Post by NuttyMonk on 2009-01-20
Hi,

Intel Celeron 3.06GHz
504MB RAM

That's all the info i can find quickly.

On the Ubuntu OS disk there are only 24 files in 8 folders.  Does that sound right to you?

I've managed to get the install disk burned now (still got to check if it worked ok, my CD drive has been sitting not getting used for about 2 or 3 years) and i was thinking of disconnecting the XP disk and going through the install process again, after formatting the Ubuntu drive, to get a clean install with no XP integration.  At least that way i can be sure that XP integration and installing through XP isn't causing any probs.

Cheers for getting back to me overdrank.  Maybe you can see a problem with anything i've mentioned here.

NM

---

### Post by overdrank on 2009-01-20
> **NuttyMonk said:**
> Hi,

Intel Celeron 3.06GHz
504MB RAM

That's all the info i can find quickly.

NM

Old and crappy laptop, pretty good specs. It may be a graphics issue. If you can identify the graphics chipset it may help. Try the live cd also and you can change the resolution with the F4 options from the start or install screen if needed. :)

---

### Post by NuttyMonk on 2009-01-20
the Graphics chipset is an...

Intel 82845G/GL/GE/PE/GV Graphics Controller

...if that makes any sense.

I'm gonna try to do the new clean (non-XP-bootlinked) install just now to see how it goes.

Cheers

---

### Post by NuttyMonk on 2009-01-20
The CD i burnt was ok.  I did the CD integrity check first to be sure.

Out of curiosity, does the Ubuntu installation format a hard disk or remove all of the old files on a hard disk before it goes through the installation process?

I did an installation with the installation CD booting up the PC as described in the Ubuntu documentation and the old Windows XP hard disk disconnected inside the PC.  The old Ubuntu installation was on there and i'm not sure if the installation would have formatted the hard disk first to get rid of the last Ubuntu install i did.

Either way, i get the same problem when the PC boots up using the Ubuntu OS.  I did a boot up of Ubuntu using the 2nd option down in the boot list (not the normal boot but the debugging boot) and i got an error message saying something about the GUI setup being wrong, but it wasn't very specific.  I'm guessing that something to do with the graphics card setup in Ubuntu isn't right.

Unfortunately, since i did that install i can no longer see the Ubuntu drive when i load up the XP OS so i can't go in and easily change any of the settings in the config files.  I may be able to do it in Ubuntu command prompt but even if i knew what was wrong and what i needed to change, i don't understand the commands in the Ubuntu command prompt so i might find it hard to make any changes even if i knew what to change.

Any advice anyone?

Cheers

NM

p.s. here is a link to the details for my onboard graphics card...
[http://www.intel.com/support/graphics/intel845g/sb/CS-009078.htm](http://www.intel.com/support/graphics/intel845g/sb/CS-009078.htm)

---

