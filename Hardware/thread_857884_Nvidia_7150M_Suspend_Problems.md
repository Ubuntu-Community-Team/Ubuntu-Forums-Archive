---
title: "Nvidia 7150M Suspend Problems"
date: 2008-07-13
forum: Hardware
---

### Post by Tibco on 2008-07-13
Can anyone with an Nvidia Geforce Go 7150M video card suspend and resume their laptop/desktop? Ive seen various threads about suspending and have tried basically everything. However, i still can't get my laptop to resume from suspend with 100% certainty. Its the video card thats the problem; when i resume from suspend, my screen sometimes just dosn't wake up, it stays blank, not even the LCD back light comes on. Now for the weird part, my laptop *sometimes* resumes without any problems at all; and sometimes it fails to resume and start up the display.

My product: hp dv6646us, running hardy 32 bit, using binary Nvidia drivers, not using compiz/beryl.

---

### Post by phidia on 2008-07-13
I think my laptop is similar to yours. I've read a lot on the suspend/resume issues at the forums here and externally too. I don't have any answers though. I'm using 64 bit btw and my laptop will resume **but** the wireless card will not come back and I've inserted scripts and read through howtos until I'm bleary eyed. sometimes usb fails to resume also. I have seen posts on blank screens you might try differnt keystrokes to wake the screen. Also check [this thread]("http://ubuntuforums.org/showthread.php?t=816852&highlight=blank+screen+resume") out.

---

### Post by chavanak on 2008-07-13
Same here guys but then i am not facing any problem with the wireless. My lappie suspends and resumes fine 3 times then the next time its an all white screen. This is solved by restarting the X

---

### Post by Tibco on 2008-07-13
> **phidia said:**
> I think my laptop is similar to yours. I've read a lot on the suspend/resume issues at the forums here and externally too. I don't have any answers though. I'm using 64 bit btw and my laptop will resume **but** the wireless card will not come back and I've inserted scripts and read through howtos until I'm bleary eyed. sometimes usb fails to resume also. I have seen posts on blank screens you might try differnt keystrokes to wake the screen. Also check [this thread]("http://ubuntuforums.org/showthread.php?t=816852&highlight=blank+screen+resume") out.

If your laptop is similar to mine, then it has a broadcom wireless card. All i had to do to get my wireless working perfectly was to follow [this guide ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). 

> **phidia said:**
> sometimes usb fails to resume also
I also have this, but i have it patched up. I have an icon on my panel that i click if i have a usb mouse or drive plugged in. It runs the command "lsusb" and that refreshes all my usb drives. Now i know this isnt a perfect solution, but i dont have usb's plugged in all the time and its easy to click it, and have all my usb drives working again. It would be nice if this happened automatically though, but since this isn't a big problem for me, im fine with it.

> **chavanak said:**
> Same here guys but then i am not facing any problem with the wireless. My lappie suspends and resumes fine 3 times then the next time its an all white screen. This is solved by restarting the X

I used to have a white screen, but it stopped after i turned off compiz/beryl, maybe thats your problem? Can you also not suspend and resume your laptop with certainty?

---

### Post by phidia on 2008-07-14
> **Tibco said:**
> If your laptop is similar to mine, then it has a broadcom wireless card. All i had to do to get my wireless working perfectly was to follow [this guide ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). 


I also have this, but i have it patched up. I have an icon on my panel that i click if i have a usb mouse or drive plugged in. It runs the command "lsusb" and that refreshes all my usb drives. Now i know this isnt a perfect solution, but i dont have usb's plugged in all the time and its easy to click it, and have all my usb drives working again. It would be nice if this happened automatically though, but since this isn't a big problem for me, im fine with it.



I used to have a white screen, but it stopped after i turned off compiz/beryl, maybe thats your problem? Can you also not suspend and resume your laptop with certainty?

I don't have a broadcom card HP put an atheros ar5007eg card in this laptop. AFAIK it can't be made to work **with** resume also functioning correctly-and man have I tried!
I'm not using compiz or any special graphical features.
Over the 6 months I've worked on getting this laptop configured and done a great deal of searching and reading I've realized I don't want to mess with it anymore. I kept trying and now I'm done.

---

### Post by Tibco on 2008-07-14
i hear you, im also getting really tired of having to try and fix my suspend problems every time ubuntu upgrades to a new Linux kernel. I guess we are stuck...until the next version of ubuntu (hopefully).

---

