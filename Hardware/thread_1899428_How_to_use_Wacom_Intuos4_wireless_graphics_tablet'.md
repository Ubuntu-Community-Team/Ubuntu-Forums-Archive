---
title: "How to use Wacom Intuos4 wireless graphics tablet's ExpressKeys?"
date: 2011-12-23
forum: Hardware
---

### Post by boxcorner on 2011-12-23
Hello

I am trying (learning) to use a Wacom Intuos4 wireless graphics tablet with Ubuntu 11.10  

So far I have only used it when connected via USB, as I am having difficulty getting a Bluetooth connection.

Ubuntu's Wacom Graphics Tablet application (System Settings > Hardware > Wacom Graphics Tablet) detects the tablet automatically, but there doesn't seem to be any way of selecting a specific Wacom model and there doesn't appear to be any way of configuring the ExpressKeys.

Could someone please tell me how to get the ExpressKeys working?

The pen works extraordinarily well in MyPaint (ie using the default settings, when connected via USB), but not so well in Gimp.  

So I followed the instructions found here: [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom") by configuring the "Extended Input Devices" but that only made it worse, so I reverted to the default.

Could someone please tell me how to configure Gimp so the pen behaves as well as it does in MyPaint?  Also, how to use the ExpressKeys in Gimp?

Thanks in advance.

---

### Post by Favux on 2011-12-23
Hi boxcorner,

The Intuous4 wireless hasn't been added to the kernel's bluez stack yet.  Przemo Firszt has come up with some initial patches for it that he asked the other Linux Wacom Project developers to review:  [http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-devel)  I don't think he's submitted them to the kernel yet.  So no bluetooth as of now unless you want to test them out.

Since ExpressKeys is a Wacom trademark in linux we call them pad buttons.  Instructions on how to use them are at the mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  That's from the HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

Instructions on updating your wacom.ko, to get the OLED patches, and xf86-input-wacom are on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") along with a sample Intuos4 xsetwacom script.  Then the OLED thread has information on how to use them.  The xsetwacom side of the OLED support hasn't been added to xf86-input-wacom yet.

You did the right thing with Gimp.  The problem is Oneiric has a bug which is why you saw the lines.  Aapo Rantalainen has a Gimp PPA where Alexia Death's patch to fix Gimp for Oneiric is already applied:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)  He has a link to the Launchpad bug report there:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  Feel free to post there or to indicate you are affected.

---

### Post by boxcorner on 2011-12-24
Many thanks for the helpful info and tips.  All right then, I will call them pad buttons in future.  Meanwhile, I'll follow the links you gave me and would certainly be interested in helping with testing, if that is of any interest.

---

### Post by Favux on 2011-12-24
Sure.

Or tablet buttons, etc.  lol  I was pulling your leg a little on the ExpressKeys thing.  ;)

I forgot to link you to the Intuos4 OLED thread:  [http://ubuntuforums.org/showthread.php?t=1380744](http://ubuntuforums.org/showthread.php?t=1380744)

---

### Post by boxcorner on 2011-12-24
Cheers

Addendum
========
I thought it would be instructive to install the software supplied, so I booted Windows for the first time for over a year and installed the v6.1.5 driver from the CD.  Then I downloaded and installed the latest driver v6.1.7-3 and control panel v6.1.7-3

Bluetooth works fine and it was interesting seeing the illuminated text alongside the buttons, for the first time, etc.  So now I know how the tablet is supposed to work, I have better understanding of what I might be able to achieve when I follow the tips above.

Just for the record, in case anyone is thinking of getting an Intuos4 wireless tablet, when I registered mine via Windows (for use with Linux), I was offered the choice of downloading one of the following aps: Adobe Photoshop Elements, Autodesk Sketchbook Express 2011, or Corel Painter SketchPad.  I wasn't sure which to choose, in any case I won't be using Windows!

Included with the tablet was a very nice "Meet the Masters - MasterClasses Vol. 1-3" training DVD.

---

