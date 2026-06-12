---
title: "Compaq V6000T"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by falonyn on 2006-12-10
I am newer to Ubuntu. I have installed it on my girlfriend's computer because she kept getting viruses on Windows. I however still use windows on my desktop. I am thinking of getting a laptop and using Ubuntu Edgy Eft and had just a couple questions before going forward.

I am looking at getting a Compaq V6000T

1. How is Edgy Eft with a Core Duo CPU? If it doesn't work well with one them I will stick with single core, but I would really like a dual core CPU for this laptop.

2. How is Edgy Eft with Intel(R) PRO/Wireless 3945ABG Network Connection? Again, if it is spotty on this then I will downgrade to the basic 802.11b/g WLAN.

Also, if there is anyone on here that has personally put Ubuntu on a Compaq of similar model I would appreciate any recommendations. This will be my first time fully ditching Windows.

---

### Post by theturtlemoves on 2006-12-10
I'm using Edgy on a HP Pavilion, which has very similar hardware, and I have had no trouble with either the dual core CPU or the 3945 wireless card. Both of them were detected fine on install and worked flawlessly. The one problem that I have had is getting the headphones to work. This might be a problem with the Compaq as well, but it's not a show-stopper for me.

---

### Post by falonyn on 2006-12-10
Thanks for the reply. 

I am hoping that there won't be a problem . . . I just need to find the exact commands once I get it to detect wireless hot spots and connect to them. I am sure a quick search of the forums should produce what I am looking for.

---

### Post by Riom on 2006-12-16
> **falonyn said:**
> 
Also, if there is anyone on here that has personally put Ubuntu on a Compaq of similar model I would appreciate any recommendations. This will be my first time fully ditching Windows.

I'm running Edgy on a Compaq V6000T.  Core 2 Duo T7200, 2GB RAM.  3945ABG network.  6 weeks old.

Installs fine, networking works OK immediately (just go to system/admin/network and activate the wireless).  I have had one case of where the wireless didn't come back to life after I switched it off (hardware switch), hibernated the machine, and switched it back on, but otherwise no problems with that.

There are a couple of install problems: the screen, and the headphone socket.  The screen initially comes up in 1024x768 stretched to fit the 1280x800, which looks ugly.  There is an easy fix for this (think it was just a config file edit), but I've forgotten what I did!

In a similar way, the headphone socket needs fixing (it doesn't disable the internal speaker).  This was much, much harder to fix but is now working OK (although the hardware volume control only controls either the speaker or the headphones, not both).  Had to compile various things from source, lots of missing dependencies etc.

I'm going to look up what I did to fix both of these and document them somewhere in case I need to reinstall.

This was also my first time fully ditching Windows, and i'm happy with this machine for that, most things just work. The multimedia support built into Ubuntu is terrible (DVD's don't play as well as on Windows, and the whole codec support is a real mess), but that's not the hardware's fault.  I do still have the Windows on here as a dual boot, but I haven't booted into it for a few weeks and that was just to compare the DVD performance.

Some things worked better than I expected: the C3180 all-in-one printer/scanner that came nearly free with it works fine, and other usb things like my mobile phone and camera connect OK also.  Firewire works fine, bluetooth recognises devices but I haven't fully tested that yet.  Haven't tested the microphones.

Downsides: the right shift key is narrower than normal so it's easy to miss.  Cooling fan comes on a little more often than I'd like.  Some people complain the touchpad is too slippy (but I turn that off and use a mouse anyway).  All in all, works fine for me.

(update)

No, it's not working now. :-(  Something has totally broken sound (both speakers and headphones), possibly (according to other threads) something in the recent kernel update.  No amount of reinstalling and recomiling sound features will get it to work.  Bear this is mind when reading reports on which laptops work: they may work now, but with an OS where the policy seems to be if it works on one computer it's safe to release without bothering to test on any others, and with an update process that doesn't have an un-update, a working system may be trashed at any time....

---

### Post by danieljay on 2006-12-31
I have the V3000z Compaq laptop and my sound did not work either when I first got my laptop. Searching all over got me the following:

Compile new ALSA greater than 1.0.13:
$ tar -xjvf alsa-driver-1.0.13.tar.bz2
$ tar -xjvf alsa-lib-1.0.13.tar.bz2
$ tar -xjvf alsa-utils-1.0.13.tar.bz2
$ cd alsa-driver-1.0.13
$ ./configure
$ make
$ sudo make install
$ cd ../alsa-lib-1.0.13
$ ./configure
$ make
$ sudo make install
$ cd ../alsa-utils-1.0.13
$ ./configure
$ make
$ sudo make install

You then have to edit your /etc/modprobe.d/sound and add the following line:
options snd-hda-intel index=0 disable_msi=1

Adding this line stops the sound from repeating over and over when you boot back into Xorg. Also you will have to put two volume controls on your kicker to control your headphones and speakers. This works great for me, I leave my speakers muted and can listen to music on my headphones. If the cord gets pulled out while I am at work it doesn't play really loud disrupting everybody. 

Hope this helps you.

---

### Post by Riom on 2007-01-02
Thanks Daniel, I did do something similar originally to get the sound to work, although I didn't need the options line.  But the early December kernel update broke it.

I have now fixed it, see the third page of [http://www.ubuntuforums.org/showthread.php?t=318259](http://www.ubuntuforums.org/showthread.php?t=318259)

---

