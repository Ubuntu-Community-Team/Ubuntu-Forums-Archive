---
title: "ATI Radeon 9800 does not work properly with Jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by chemamar on 2009-04-26
I have an ATI Radeon 9800 pro that worked more or less with Ubuntu 8.10, after upgrading to 9.04 does not work properly. Maybe the problem is with my card, because with 8.10 I had to include in xorg.conf in section "device" the option "SWcursor" "on" to make it work properly and avoid the mouse pointer flickering.

But now with the new xorg.conf that option doesn´t work for me, whenever I include it as I did with 8.10 my system cannot log in, I write once and again my login and password, the system tries to start but fails and goes back to the log in.

I don´t understand why 8.10 could support properly this option and 9.04 doesn´t.

Besides, firefox displays poorly, something to do with fonts?

I have manged to see properly videos with vlc.

Any advice?:biggrin:

---

### Post by happyhobbit on 2009-06-07
From the unofficial ATI wiki

Which cards does ATI no longer support? The ATI Radeon 9500-9800, X300-X2100, Xpress. See the complete list here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.5. !!!SO BE CAREFUL!!! 

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers)

So I'm about to downgrade again as I need the TV-Out to work...

---

### Post by Vincentoo on 2009-06-20
Anybody got a workaround/solution to this?
Or any idea if there are some plans to fix this in the future?

Or... Radeon 9800 is too old (:lolflag:) and that's it, the message is use the previous release?

---

### Post by Mark Phelps on 2009-06-20
> **Vincentoo said:**
> Anybody got a workaround/solution to this?
Or any idea if there are some plans to fix this in the future?

Or... Radeon 9800 is too old (:lolflag:) and that's it, the message is use the previous release?
AMD/ATI has not indicated any plans at all to resurrect support for their older cards in the future, so basically, there are no plans from the vendor for "fixing" this.

As to the open source drivers, they are constantly being improved, but usually, that is to fix bugs and add features in the newer cards.  So, if the open source drivers don't work with your card, you're pretty much out of luck.

---

### Post by wpshooter on 2009-06-20
> **chemamar said:**
> I have an ATI Radeon 9800 pro that worked more or less with Ubuntu 8.10, after upgrading to 9.04 does not work properly. Maybe the problem is with my card, because with 8.10 I had to include in xorg.conf in section "device" the option "SWcursor" "on" to make it work properly and avoid the mouse pointer flickering.

But now with the new xorg.conf that option doesn´t work for me, whenever I include it as I did with 8.10 my system cannot log in, I write once and again my login and password, the system tries to start but fails and goes back to the log in.

I don´t understand why 8.10 could support properly this option and 9.04 doesn´t.

Besides, firefox displays poorly, something to do with fonts?

I have manged to see properly videos with vlc.

Any advice?:biggrin:

All that is sort of strange because I am using an ATI Radeon 9600XT in my Ubuntu machine and it works just fine.  Am using 9.04.  My ATI card is an actual ATI built card and not one of those "Power by ATI" cards.  Which is yours ?  I wonder if that could have anything to do with your problems ?

On my computer I just installed Ubuntu from the Live CD and video works, I don't attempt to install anything that the Ubuntu install doesn't do itself.  I have found that if you attempt to change what Ubuntu installs, you are probably asking for trouble !!!

---

### Post by Mark Phelps on 2009-06-21
> **wpshooter said:**
> All that is sort of strange because I am using an ATI Radeon 9600XT in my Ubuntu machine and it works just fine.  Am using 9.04.  My ATI card is an actual ATI built card and not one of those "Power by ATI" cards.  Which is yours ?  I wonder if that could have anything to do with your problems ?

I never said it wouldn't work -- the open source driver works OK for me, too.  I just said that if it didn't work, you're out of luck -- because there is no restricted driver that WILL work. And, mine is an actual ATI card, not a third-party card using ATI chips.

> On my computer I just installed Ubuntu from the Live CD and video works, I don't attempt to install anything that the Ubuntu install doesn't do itself.  I have found that if you attempt to change what Ubuntu installs, you are probably asking for trouble !!!
That's because Ubuntu makes a best effort to automatically install the proper driver based on the hardware it detects.  And, you're right, when folks get into trouble is when they try to force other drivers onto their system -- drivers that did not get installed automatically.

---

### Post by chemamar on 2009-06-23
> **wpshooter said:**
> All that is sort of strange because I am using an ATI Radeon 9600XT in my Ubuntu machine and it works just fine.  Am using 9.04.  My ATI card is an actual ATI built card and not one of those "Power by ATI" cards.  Which is yours ?  I wonder if that could have anything to do with your problems ?

On my computer I just installed Ubuntu from the Live CD and video works, I don't attempt to install anything that the Ubuntu install doesn't do itself.  I have found that if you attempt to change what Ubuntu installs, you are probably asking for trouble !!!

Thanks for answering. Things have changed a lot since I needed help. I have found some code that improves hugely the performance of my card. For the open source just add these lines in xorg.conf and enjoy!
```
Section "Device"
	Identifier	"Configured Video Device"
        Option "EnablePageFlip" "True" #see http://ubuntuforums.org/showthread.php?t=1166846
	Option "MigrationHeuristic" "greedy"
	Option "AccelMethod" "EXA"
        Option "AccelDFS" "true"
	Option "RenderAccel" "on"
        Option "AGPMode" "8"
	Option "FBTexPercent" "0" # see http://foros.ubuntu-cl.org/viewtopic.php?p=37255

EndSection

```

All the credit here:
[http://ubuntuforums.org/showthread.php?p=7235254#post7235254](http://ubuntuforums.org/showthread.php?p=7235254#post7235254)

---

### Post by Vincentoo on 2009-06-29
Hello,

I also managed to get the open source driver working with my Radeon 9800 Pro and TV-OUT (since the goal is to run MythTV on TV). I had to write a little script to issue some "xrandr" and "xattr" commands and now my final issue is to convert these into options I can put in my xorg.conf to have them statically enabled...

Anybody knows what could be the equivalent of:
```
xvattr -a XV_CRTC -v 1
```

---

### Post by MaWi WoWi on 2009-06-30
For me (9800PRO 8x) the best settings were the following. Note: AGPMode 8 was significantly slower than 4.
 
```


Section "Device"
        Identifier      "Configured Video Device"
        Option "MigrationHeuristic" "greedy"
        Option "AccelMethod" "XAA"
        Option "AccelDFS" "true"
        Option "AGPMode" "4"
EndSection


```

---

### Post by Vincentoo on 2009-07-16
Using  mix of these options I now have the TV out working quite well. The only remaining issues I still see are:
[LIST]
[*]The use of the shell xvattr... that I had to put in a script which is executed when I log in. No way to have it statically in the xorg.conf???
[*]Sometimes I get some artifacts in videos in white zones.
[/LIST]

---

### Post by csabo2 on 2009-07-16
I have a machine with a 9800 pro in it. Just face the inevitable, linux HATES this card.

---

### Post by Mark Phelps on 2009-07-16
> **csabo2 said:**
> ... linux HATES this card.

Hey, let's be fair here!  If Linux really HATED this card, there would be no drivers at all for it.

It was the card vendor that dropped support, not Linux or Canonical.  AMD also dropped support in Vista for this card, and provides no drivers for Seven for this card.

So, if you want to "point the finger of blame", do so at AMD/ATI.  At least Canonical (and others) are providing some drivers that continue to work in Linux.

---

### Post by Violasoundsgood on 2009-07-29
Hello fellow Ubuntu / Ati Radeon 9800 pro users!

Is there anyone who is willing and has the time to help me with this video card?  It seems that the people in this thread have met with some success with this card.  I am a newbie to linux, but I learn quickly.

I would love to have the tv out capabilities, etc. of this card, but I just don't understand yet about editing config files.

In order to install ubuntu Jaunty, I had to enable the "safe graphics mode"  so I don't know if i'm really out of that mode or not.  I'm assuming that I have the open source driver installed, even though I didn't do it.  

I have tried installing the proprietary driver, but it makes my system hang at log on.  

Again, does someone have the time, and is willing to share some of this advice in slightly simpler terms?  Thank you so much in advance.

David

---

### Post by Violasoundsgood on 2009-07-31
So I am beginning to understand a little bit.

I figured out where the xorg.conf file was.  I also found out the reason I'm seeing my display at all is because i'm using the vesa driver.  

There was a backup of xorg.conf, and I figured out how to restore from it in grub  in case I screw up too badly.

Looking at synaptic package manager, it would seem that the open source driver IS installed, as well as a radeon backlight function (this isn't a laptop, though), the open source driver, and the "ati wrapper"

When I try and change the settings in xorg.conf, like changing driver to "ati" my screen goes blank when GNOME loads, but it otherwise appears to be wokring fine, because it plays the startup wave file. 

So what am I still doing wrong?  Should I copy and paste my xorg.conf file?  it's not very long.

---

### Post by Mark Phelps on 2009-08-01
> **Violasoundsgood said:**
> I have tried installing the proprietary driver, but it makes my system hang at log on.  

Just how many times do we have to tell folks that there is NO restricted driver for their card that works under 9.04 before that is understood???

The open source driver is installed BY DEFAULT -- and that is all there is!!

It is pointless to keep posting again and again when "it is what it is."

---

