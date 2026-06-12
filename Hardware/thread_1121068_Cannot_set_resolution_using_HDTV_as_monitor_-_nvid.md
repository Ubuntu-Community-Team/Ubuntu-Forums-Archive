---
title: "Cannot set resolution using HDTV as monitor - nvidia drivers make thing worse!"
date: 2009-04-09
forum: Hardware
---

### Post by heyho on 2009-04-09
Hello all.

I am in the process of trying to set up an old desktop box as a basic means of watching divx/xvid on the main television.

When connected up to the tv(via vga), I get a max selectable res of 800x600, although the splash screen is 1024x768 (the tv tells me this.)

My first thought was to activate the nvidia drivers - this actually made things worse - max res was now 640x480, so I de-activated them.

Xrandr shows the max res to be the same (800x600), and forcing a higher mode does not work, as they are not available.

Thinking that this may be a quirk of the display, so I tried it on 2 other LCD TVs in the house, with the same results.  When plugged into my trusty old GNR 15" LCD 4:3 monitor, all is good - lots of resolutions are available, up to the native 1024x768 that the monitor requires.

It seems that the TVs either don't report the EDID info, or report it incorrectly.  The TV is a 26" sony bravia, which accepts 1280x768 over vga (according to the manual).  If I specify the horizontal sync and vertical refresh rate in xorg.conf, the log out and back in, I get the correct res immediately, albeit with a very slight flicker to the screen.  Setting the "ignoreEDID" option doesn't appear to help.  I should also mention that windows gives lots of higher resolutions.

The card is a Geforce 2 400mx 64mb, and I have also tried a geforce3 card, with the same results. I am loathe to purchase another card, in case it is the same!

Any advice? (fresh and updated hardy install)

---

### Post by Mokoma on 2009-04-09
> **heyho said:**
> Hello all.

I am in the process of trying to set up an old desktop box as a basic means of watching divx/xvid on the main television.

When connected up to the tv(via vga), I get a max selectable res of 800x600, although the splash screen is 1024x768 (the tv tells me this.)

My first thought was to activate the nvidia drivers - this actually made things worse - max res was now 640x480, so I de-activated them.

Xrandr shows the max res to be the same (800x600), and forcing a higher mode does not work, as they are not available.

Thinking that this may be a quirk of the display, so I tried it on 2 other LCD TVs in the house, with the same results.  When plugged into my trusty old GNR 15" LCD 4:3 monitor, all is good - lots of resolutions are available, up to the native 1024x768 that the monitor requires.

It seems that the TVs either don't report the EDID info, or report it incorrectly.  The TV is a 26" sony bravia, which accepts 1280x768 over vga (according to the manual).  If I specify the horizontal sync and vertical refresh rate in xorg.conf, the log out and back in, I get the correct res immediately, albeit with a very slight flicker to the screen.  Setting the "ignoreEDID" option doesn't appear to help.  I should also mention that windows gives lots of higher resolutions.

The card is a Geforce 2 400mx 64mb, and I have also tried a geforce3 card, with the same results. I am loathe to purchase another card, in case it is the same!

Any advice? (fresh and updated hardy install)

yeah easy advice. update to intrepid/jaunty beta. buy a moderatly modern card (6800+) or something. the drivers for those cards are WAY out of date. nvidia linux drivers have come a long, long way recently. anyway it can be hard enough setting up tv out on a windows machine, let alone linux O,o

---

### Post by heyho on 2009-04-10
I think you are right - but rather than a new card, I'll probably go for a new setup with an HDMI motherboard.

I'll have a go with the final Jaunty when it's released, or stick with my workaround for the time being.  Cheers.

---

### Post by Mokoma on 2009-04-10
actually dude, there may be a workaround. go into add/remove and search for a program called nvtv. its a really good little program for controlling tv out. i used to use it with my old 5700 to watch dvds on the household big tv :D

---

### Post by heyho on 2009-04-10
Cheers chap, will give that a go.  It's not the end of the world - like I say I can achieve the correct res, but it would be nice to be able to use it on different televisions without all the headache that goes into finding the timings for unbranded displays.

The idea was to make use of a redundant box, not spend more on it - oh well!

---

### Post by Mokoma on 2009-04-10
lol no probs man. but its not just linux that has this kinda problem. my 5700 was/is a personal cinema card which can do tv in/out and god knows what else. but because of service pack 2 on windows xp all the extra functionalities where unuseable. but when i switched to gutsy i could use everything :D

good luck anyway (y)

---

### Post by heyho on 2009-04-24
It would appear that my problems may have been caused by the el-cheapo 3m VGA lead I purchased from ebay.

I was messing about this evening, but using a generic "came with monitor" lead, and I realised that I instantly had a load more res options to choose from!

Tried the same lead with the sony bravia, and whammo - into res settings and straight to 1280 x 768, clear as a bell and no flickering.  Lesson learnt.:)

---

