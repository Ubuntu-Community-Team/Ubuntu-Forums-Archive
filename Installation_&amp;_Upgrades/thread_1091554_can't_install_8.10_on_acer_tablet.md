---
title: "can't install 8.10 on acer tablet"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by kuritsubaji on 2009-03-09
I'm trying to install 8.10 on my acer travelmate C204 tablet.

CD will boot to the installation menu, but after I select 'install ubuntu', the system freezes on the next screen (ubuntu progress bar) after only a few seconds and requires a hard reboot.

I've tried safe graphics and OEM mode with the same results.

Selecting 'try ubuntu..' yeilds the same results as well.

I've even tested the memory and checked the CD for errors-- nada.

Does it have something to do with the acer partition?

---

### Post by t0mppa on 2009-03-09
Somewhat equal problems here on Acer Travelmate 7530, suggesting it could be an issue with Acer hardware or software.

I can boot from the Ubuntu 8.10 LiveCD, but when trying to install (normal, safe graphics mode both the same) or run (ie. "Try Ubuntu without making any changes...") from the LiveCD, getting to Xwindows fails and it just drops me into a text based console.

And yes, I tried reburning the CD with the slowest possible speed, checking the MD5 checksums, checking CD integrity with the option from Ubuntu start menu and a bunch of other things I googled up, which didn't help at all. Later I figured out the problem isn't in the CD, since I tried it on another computer and everything works just fine there.

So, I would appreciate it, if someone could toss in some pointers on how/where to find what's wrong.

---

### Post by kuritsubaji on 2009-03-09
t0mppa wrote:

"...Later I figured out the problem isn't in the CD, since I tried it on another computer and everything works just fine there."

--

I also used the same disc to install on a completely different machine and did so without any problems, whatsoever.  


UPDATE:

I tried installing to my C204 using the Alternate CD and was able to make progress, to a point.  

I select 'Install Ubuntu', go through the language and keyboard dialogues, the installer detects the CD-ROM, loads the extra components, detects the network hardware and then just locks up with a blank blue screen.  

In normal mode, it will lock up with the HDD light on--for hours.  

In OEM mode, it locks up at the same place, but with the HDD light off.

Also, if a cable is plugged into the LAN port, the status/activity lights are both on (activity blinking), but both go out when the system locks up.

---

### Post by t0mppa on 2009-03-10
Well, my issue appeared to be with Graphics drivers (see [http://ubuntuforums.org/showthread.php?t=1092629]("http://ubuntuforums.org/showthread.php?t=1092629")).

Guess yours is a bit more complicated.

---

### Post by kuritsubaji on 2009-03-11
Graphics may be the culprit here as well.  The tablet  uses the nVidia GeForce Go 6200 and I read a post where someone else was having a problem with another in the 6000 series.

Although, with the network lights going out when it locks up, could the problem  be with the network adapter?  I find this unlikely since the status lights showed an active connection  before it crashed.

I've come across a couple of other posts where someone has successfully installed ubuntu on the exact same tablet only with issues later in setting up the wireless or pen functions.  Yet, I can't even get the desktop installed.

Does anybody have any clues?

---

### Post by t0mppa on 2009-03-11
I'm by no means an expert on this, but since the alternative install happens purely in text mode, I'd argue it isn't a graphics issue that's stopping you there.

---

