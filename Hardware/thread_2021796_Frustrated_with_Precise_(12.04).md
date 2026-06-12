---
title: "Frustrated with Precise (12.04)"
date: 2012-07-09
forum: Hardware
---

### Post by SimpsonTruckDriver on 2012-07-09
First, it was no wireless ([http://ubuntuforums.org/showthread.php?t=2017612](http://ubuntuforums.org/showthread.php?t=2017612)), which has not been fixed yet ](*,)

Now, my SOUND does not work! I get the bongo sounds when the login screen comes up, and it works fine in Windows Vista, but not in 12.04. ](*,)

When I type:[INDENT]alsamixer
[/INDENT]It shows nothing is muted. It's set to 100% (high). So, when I type:[INDENT]aplay -l
[/INDENT]I get:[INDENT]****** List of PLAYBACK Hardware Devices ******
**card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]**
**  Subdevices: 1/1**
**  Subdevice #0: subdevice #0**
**card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]**
**  Subdevices: 1/1**
**  Subdevice #0: subdevice #0**
[/INDENT]Typing:[INDENT]lspci | grep Audio
[/INDENT]also says[INDENT]**00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)**
[/INDENT]Typing[INDENT]alsactl --version
[/INDENT]says[INDENT]**alsactl version 1.0.25**
[/INDENT]When I had 10.04 LTS, both worked fine. But, like I said in the no-one-has-fixed post above, I installed on a "clean" partition, and now, neither works. Almost makes me want to get rid of 12.04 and find an earlier 11.xx version and hope that works. Or find (I no longer have) a 10.04 LTS.

TS

---

### Post by ahallubuntu on 2012-07-10
I have an old E1505 - some physical issues but it still works, has 10.10 on it plus XP.  I haven't tried 12.04 on it yet, however.  Mine only has a 32 bit CPU and I only have a 64 bit live CD at the moment, so I can't try it immediately.

The first thing to fix is your crappy Broadcom wireless card.  Broadcom cards have terrible Linux support issues.  Dump it and get an Intel card - that what I have always had in mine.  It came with an Intel 3945ABG card and I replaced it with an Intel 5100 WiFi Link card - a much better card with N wireless.  

You want a full-height card not a half-height: "INTEL WIFI LINK 5100 512AN_MMW."  Search for that on eBay.  If you are in the US, get the Toshiba version a place in San Diego is selling for $7.94 USD shipped.  This card will work great in your E1505 in Linux (and Vista but you'll have to install the Intel driver).  DO NOT get an HP or Lenovo version of the 5100 card (it will work in your Dell in Ubuntu but not in Windows) - just get a Dell, Toshiba, or generic Intel card.  I suggest you get a used one not a "new" one from Asia - I've had bad luck with engineering samples on those or incorrect part numbers.

The card is under the keyboard on your E1505.  Pretty easy to remove: flatten out the screen, pop up the protector above the keyboard, unscrew the keyboard (you can leave it plugged in).  Once you get to the card, the hardest part is getting the two antenna wires off the card; just use a needle nose pliars and do it very carefully.  Snapping the wires on the replacement card is much easier.

As for the sound: can't help you with that, but if you get the "login" sound that probably means it's not a hardware issue.  Maybe something is muted somewhere.

---

### Post by mastablasta on 2012-07-10
have you tried setting the sound output to stereo analog in sound settings ?

---

### Post by SimpsonTruckDriver on 2012-07-10
The Sound Settings only shows:

[B]Digital Output (S/PDIF)
*Built-In Audio*[/B]

In terms of the failure to make Ubuntu 12.04 LTS accept my wireless card, I will probably stick with my Verizon Wireless MiFi 2200 (works fine through USB). It works fine in Windows Vista, just like sound works fine in Vista.

TS

---

### Post by SimpsonTruckDriver on 2012-08-01
Any ideas?

TS

---

### Post by trulynon on 2012-08-01
I have the same sound codec in my Probook 4530s and I've experienced the same problem as you have - no sound from the internal speakers. However, the headphones worked fine. Such situation has happened to me for the first time since I own this laptop. 
 
How i solved this problem? Actually I don't know, sound is being played after I a few times removed the jack from headphones and plugin in again when I back home. [I wrote a post ]("http://en.community.dell.com/support-forums/laptop/f/3517/p/19427228/20135091.aspx")about this issue on Dell forum since I find out that only these kind of audio codecs (Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]) appears to have this issue. 
 
Hope you'll find a solution.
 
EDIT: For me the problem appers on both systems - Windows and Linux. So this must be some kind of a hardware issue. Hoverver now is OK. I'll suggest to play with a headphone jack on on Windows.

---

### Post by SimpsonTruckDriver on 2012-08-24
Unfortunately, it's a software issue. It works fine in Windows, but NOT in Ubuntu. It worked in 10.04 LTS, but no longer works.

ST

---

