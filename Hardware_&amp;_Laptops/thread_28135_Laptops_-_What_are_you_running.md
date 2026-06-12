---
title: "Laptops - What are you running?"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by gadfly on 2005-04-18
I am looking around for a laptop/notebook  and I was hoping to hear some success stories around notebooks running ubuntu?

Any info?  recommendations? . . .

Thanks

gadfly

---

### Post by kiddo on 2005-04-19
I have a (quite old, bought it from a friend) Dell Inspiron 5000. That's 5 years old (there was no cdrom drive, and win98 on it!) but it's a Pentium 3. Had to upgrade the RAM and get a drive, but otherwise it's pretty good. As for experience with hoary, I'm just amazed. Back in september 2004, Fedora Core 2 was not THAT good with it. Ubuntu flies, and everything worked out of the box for me (except that linksys wireless card, which I just made work today by reading the ndiswrapper howto in the ubuntu.com/wiki). The touchpad was a bit misconfigured, because it has too much acceleration, so the only way I got was to manually edit my xorg.conf. Otherwise, the pcmcia lan/wlan card hotswapping works very well, almost as well as windows XP. I'm impressed. Hibernation is working wonders too. I just noticed it suddenly started slowing down the hard drive when on battery (it never slows down when on power). But maybe that's because I changed something in the bios recently.

---

### Post by krrh on 2005-04-19
I'm running a Dell Inspiron 1000. Overall, the experience has been positive. The machine works with standard Ubuntu, but I've had issues configuring the included Dell Truemobile 1350 wifi card. It's of the famously difficult Broadcom variety.

ACPI events have been an issue as well. Sleep and hibernate both malfunction on resume, and I have yet to find any fixes through Google or the forums.

Otherwise, installation and hardware recognition has been a snap, and this laptop can usually be found on the Dell outlet site for under $500. (Dell drops new units into its outlet inventory near the 47 minute of every hour, if you're serious about nabbing one. They usually sell out within a few minutes.)


Good luck finding a laptop.

---

### Post by tmowerman on 2005-04-19
I am runnning a HP omnibook xe4500.  I have had a few issues though.  The toucpad needed manual configuration, as horizontal scrolling had issues with firefox.  Installing wireless lan card was easy enough with ndiswrapper.

The annoying problem is that xorg does not want to support the graphics card correctly, so under warty I had tv out, and workable 3D.  Upgrading to Hoary stopped this!!!

So my advice would be, don't get a laptop with an ati mobility m6 graphics card.

---

### Post by Nano on 2005-04-19
[QUOTE=kiddo]I have a (quite old, bought it from a friend) Dell Inspiron 5000. That's 5 years old (there was no cdrom drive, and win98 on it!) but it's a Pentium 3. Had to upgrade the RAM and get a drive, but otherwise it's pretty good. As for experience with hoary, I'm just amazed. Back in september 2004, Fedora Core 2 was not THAT good with it. Ubuntu flies, and everything worked out of the box for me (except that linksys wireless card, which I just made work today by reading the ndiswrapper howto in the ubuntu.com/wiki). The touchpad was a bit misconfigured, because it has too much acceleration, so the only way I got was to manually edit my xorg.conf. Otherwise, the pcmcia lan/wlan card hotswapping works very well, almost as well as windows XP. I'm impressed. Hibernation is working wonders too. I just noticed it suddenly started slowing down the hard drive when on battery (it never slows down when on power). But maybe that's because I changed something in the bios recently.[/QUOTE]
 Medion 40100.
It always worked perfectly. Graphic card (nvidia 64mb) detected, DVD writer working, etc.

---

### Post by Psquared on 2005-04-19
Brand new Toshiba here. 35X331 with Pentium M 1.5 ghz and 512 mb ram.

I had FC2 on a desktop last year before I took it off. It required too much tweaking.

In this case I used the Linux Rescue CD and QT-Parted to divide my 60 gig harddrive in half and installed Ubuntu Warty. It could not recognize my wireless adapter during the installation so I just plugged my laptop directly to my router using and ethernet and ran the installation. After that I was able to configure the wireless adapter.

Warty ran perfect the first time on my laptop. Absolutely no problems. Even the touchpad seems calibrated correctly. I have the extra wide display and it even picked the correct resolution without my tinkering.

I have not had a single freeze/lockup and I have pushed it pretty hard. Setting up my HP 5550 was a breeze - although I could not get it to print underlined characters.

I paid 999.00 for this laptop at Best Buy. (after rebates of 250.00) It was well worth it and I have not used Windows in awhile.

I have had trouble with dist-upgrade to Hoary, but I am so content with Warty right now that I really don't care.

Oh, and the new Xfce with its own binary installer simply is the best. The menu structure is still a bit awkward and Xfce 4.2.1.1 does not seem quite as fast as earlier versions, but its a pretty good substitute for Gnome - even if its just for variety.

Sorry to get - off topic here. Hope you find a good laptop.

---

### Post by yusufk on 2005-04-19
Hey there,

I ran Warty, Hoary and now even risking Breezy on a Dell D800. So far so good, had some initial Sound and Wireless issues with Warty but it was sorted out quite promptly. Hoary ran like a dream, managed to get Twinview running on my nvidia card and all is beautiful. 

I use the laptop with a docking station and I must say it responds well, even to docking and undocking.

So there, hope that helps with the decision, my advice: Best way to decide is to just go for it!

---

### Post by littleking on 2005-04-20
Thinkpad T41

EVERYTHING works outta the box

---

### Post by dataw0lf on 2005-04-20
The Compal ACL 10.  Great laptop, everything works, with a bit of tweaking.  Still need to get off my ass and dist-upgrade though.

---

### Post by ghost on 2005-04-20
I run it on my Toshiba, it works perfectly.

---

### Post by Eraser on 2005-04-20
Averatec 3250H1.  Almost everything works out of the box.

I haven't tested the modem or the PCMCIA card slot.

2D video works, no DRI acceleration.

Wifi does not work out of the box, however, following the howto at:

[http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)

does the trick.

Eraser

---

### Post by StacyWebb on 2005-04-20
Dell Ispiron 9100 (wide screen), ati, dvd writer all of this works (including 3d and doom3)
 :smile:

---

### Post by martinko on 2005-04-26
[QUOTE=littleking]Thinkpad T41

EVERYTHING works outta the box[/QUOTE]
 For me, hibernation/suspend does NOT work on the T41 -- how did you manage ?

Martin.

---

