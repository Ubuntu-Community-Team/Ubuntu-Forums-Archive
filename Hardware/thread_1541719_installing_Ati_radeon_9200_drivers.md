---
title: "installing Ati radeon 9200 drivers"
date: 2010-07-29
forum: Hardware
---

### Post by cqc on 2010-07-29
hi, i have old ati 9200 and i need to install drivers because i cannt watch any flash video its too slow and crapy. Tried to install drivers from ati site with .sh command but nothing this is what i get

stojakov@stojakov-desktop:~$ sh '/home/stojakov/Downloads/ati-driver-installer-8.28.8.run' 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
it seem to me that i need some x server. Help im using ubuntu 10.04 desktop 32bit
thanks

---

### Post by james_xxx on 2010-07-29
You cannot use ATI proprietary drivers on a card that old. It has not been supported for a long time.

You have no choice but to use the Open Source driver. However, you should be able to play flash videos with no problem, in most cases.

It may be that you will need to have Compiz (or whichever Composite manager you might be using) off, in order for them to play very smoothly.

You would be really well-advised to do a little reading in a case like this before you go after a solution. Once you get used to approaching things that way, it will save you a fair bit of frustration.

Good luck!

---

### Post by Yellow Pasque on 2010-07-29
Your card is no longer supported by recent ATI proprietary drivers. You're trying to install an ancient version of the ATI drivers, which won't run on modern versions of Ubuntu. Run the commands in this section to clean the failed driver install: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

Flash video using the Flash plugin isn't accelerated very well on Linux, no matter what driver/GPU you use. It's very CPU intensive, so get a better CPU if possible. You can also use scripts like this to replace Flash with a native video player on popular video sites: [http://ubuntuforums.org/showthread.php?t=1487327](http://ubuntuforums.org/showthread.php?t=1487327)

---

### Post by darolu on 2010-07-29
Yes, as james_xxx said ATI no longer supports your card, I have a (quite) similar one (9550) and I run it with the open driver very well, so I think your problem may be something else than your video card's driver, it most likely has to do with your RAM or VRAM, less than 1GB of RAM, less than 256MB VRAM can cause it, of course depending on other factors (like processor and whatever you're using to play the video) so my recommendation is to kill unnecessary processes. Compiz and other compositing software (Desktop Effects) are quite 'heavy' and killing it is recommended when playing video games or playing large/hd videos, install this app to switch compiz on and off with a single click:

[http://forlong.blogage.de/en/entries/pages/Compiz-Switch](http://forlong.blogage.de/en/entries/pages/Compiz-Switch)

Read the entire article, if you use 10.04 an extra line must be run.

---

### Post by cqc on 2010-07-29
okay, then how to install open source drivers?

---

### Post by Yellow Pasque on 2010-07-29
> **cqc said:**
> okay, then how to install open source drivers?
THey're already installed.

---

