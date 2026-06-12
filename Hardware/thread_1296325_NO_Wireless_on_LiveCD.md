---
title: "NO Wireless on LiveCD"
date: 2009-10-20
forum: Hardware
---

### Post by Timmi on 2009-10-20
After trying out some Live CDs, I'm surprised that I don't automatically get WiFi detection on my Toshiba core2duo Laptop with Ubuntu.  Other distributions' live CDs (Mint, Knoppix, and some others) auto-detect and auto-configure and show me a list of available wireless connections available, and all I have to do is select mine, enter my WPA key, and off I go. 

I haven't been able to, for the life of me, find this in the Ubuntu 9.10beta Live CD when I boot with it. 

With the Live CD, what am I doing wrong? and WHERE am I supposed to look?  (and even more puzzling, WHY doesn't the LiveCD automatically configure this - will the final version have this implemented?)  Mint7, which is built on Jaunty, has a LiveCD that auto-detects and auto-configures automatically! 

---------------------------------------------------------------------------------------

Backgrounder (may same some questions and thread back and forth later on): 

Frustrated with lack of webcam support, complexity of Voip configuration, more versatile laptop power management, I'm eager to try the new Ubuntu 9.10 (beta at the time of this writing) of which the Debian6 core addresses these issues. 

Currently, I use Linux Mint 7, which is 101% Ubuntu 9.04 (ubuntu with all the multimedia codecs and some extra polish added to it), but ALWAYS has a month to several months lag time before the equivalent release comes out, and I don't want to wait for these vital features that are in Debian6. 

I don't want to mess with terminals and cryptic technogeek commands - no offense intended, I just don't want to right now, don't have the mindset for that, but I definitely will takle that in the future. 

And yes, I did search the forums before posting, but first of all, 1600 pages of posts relating to my search was intimidating, and I doubt they relate to the 9.1 beta anyways, as in the past, when I tried it, it seemed to me that it did work in a past version, out of the box. 

Thanks for your patience with a newbie.

---

### Post by Giblet5 on 2009-10-20
It would help to know which Toshiba laptop you're using.

They make two or three now, I think. ;)

And 9.10 is beta for another 10+ days.........

Try Jaunty.

---

### Post by Timmi on 2009-10-20
I already HAVE Jaunty within my Linux Mint 7, and Mint7 does that just fine. 
 
The reasons why I'd like to switch to Ubuntu 9.10 are the following: 
* doesn't have the months update delay of Mint (although Mint IS Ubuntu except for some extras added to it - nothing else is modified or taken away - Mint waits for the Ubuntu final release before implementing it's improvements)
* better laptop power management
* integrated webcam driver 
* other improvements (improved intel video driver, voip, etc.)

---

### Post by cwbar_1 on 2009-10-20
The first thing you need to do is enable your wireless.  System > Administration > Hardware Drivers.  See if the driver for your card is listed.  If it is, click on it, and then click "Activate."  When you are told to enter the password to "Activate," leave it blank and click Authorize.  It will apply the changes.  Then left click on the wireless icon, and select your network.

---

### Post by Timmi on 2009-10-21
Thank you for that suggestion. It's really not obvious, for a new user of this OS to find that (especially since the menu arrangement is rather unique). 
 
I went to System, Administration, Hardware Drivers... and much to my surprise, the list was EMPTY! Both parts of the box, the top part, and the bottom part, were **empty** 
[SIZE=1](I'm assuming the top would be for manufacturer and the bottom a list of models from that mfg). I guess I'll have to wait for this to come out of Beta before I can evaluate it.[/SIZE] :-( Bummer... I'm really eager to get that increased capability for my laptop. 
 
Oh, and BTW, my Toshiba core2duo uses a CENTRINO chipset, pretty much the most prevalent, and the most common Intel Wireless Card in laptops with a Centrino chipset. I really don't understand why detection for even the most common devices isn't even enabled by default.  It's little details like these that make me understand why they had to come out with **Linux Mint ubuntu**. 
 
I'm writing all of this because they have requested feedback on the 9.10 beta. 
In the hopes that they'll come to their senses and have some auto-configuration built-in for other users (as I know where to look now).

---

### Post by Timmi on 2009-11-01
the final release of 9.10 works fine.  

doesn't have the problem that the prerelease 9.10beta live cd had.

---

