---
title: "Can't get sound on Sound blaster audigy"
date: 2009-03-04
forum: Hardware
---

### Post by Spoletta on 2009-03-04
I know this has been asked lots of times, but searching trough the forum i could not find a solution.

So, I just installed ubuntu 8.0.4 and works perfectly for everything except that i don't get any sound.
If i run  lspci i get the following:

02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

so it should be installed.

This is as far as i get, i'm totally noob about linux.

I'm using earphones.

Anyone has any advice?

Thanks in advance.

---

### Post by bazzer on 2009-03-13
You might not be adjusting the correct device from the mixer - go to System>Preferences>Sound and experiment with different settings. When you know which device is working, double click your volume control and select the device from the top drop down list.

---

### Post by narmoture on 2009-04-14
I have the exact same problem! If I plug in my speaker system to the motherboards connection, I can get sound from the onboard (integrated) sound chip. 

But I don't want that! I want to use my Creative Labs SB Audigy card!
Although according to [this guide]("http://ubuntuforums.org/showthread.php?t=843012"), it's Creative Labs being stingy:

> **Creative Soundblaster Cards**
Creative cards have been nothing but a big pain in Linux forever. Creative has been completely unwilling to make any technical information about their cards available to driver the open source community so drivers have had to be reverse engineered. Creative has released a few proprietary Linux drivers but these have proven to be generally unusable. Just recently, after the latest fiasco with their proprietary X-FI driver, Creative has thrown in the towel and announced that they will make technical information available so the open source community can write proper drivers. OSS4 has drivers for the X_Fi cards now but there is no ALSA driver included in the ALSA packages yet. 

I too have checked many posts and have set my default card to my Audigy card, but nothing helps! Except plugging in the sound system to my motherboard (you might try that, btw...):mad:

---

