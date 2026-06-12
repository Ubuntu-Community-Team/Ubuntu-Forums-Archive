---
title: "No sound using X-Fi Xtreme Audio card"
date: 2009-12-19
forum: Hardware
---

### Post by OzuYatamutsu on 2009-12-19
I have been trying for a while to get sound working, but have had no luck so far.
Under System->Preferences->Sound, I see under the "Hardware" tab:

0802 (my webcam microphone)
Internal Audio
[SB X-FI Xtreme Audio] CA0110-IBG

I've tried installing the snd-hda-intel drivers and updating ALSA, but nothing has worked so far. I'm using Ubuntu 9.10 and ALSA version 1.0.21 and would appreciate any help.

---

### Post by erixoltan on 2009-12-19
I am having almost exactly the same problem.  I am using Ultimate Edition 2.5 which is Karmic 9.10 -- mine is 64 bit.  I have set the device to analog stereo output, and I have SB X-Fi Xtreme Audio CA0110-IBG listed as the device.  (Maybe the solution will be the same for both of us?)  My system is a dual-boot and the sound works in Windows 7 so I know the sound card is OK.

---

### Post by erixoltan on 2009-12-19
I just tried all the steps here:

[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

The steps worked (I had to use sudo bash instead of su) but no sound in my case.  Apparently this has worked for others.

---

### Post by OzuYatamutsu on 2009-12-19
> **erixoltan said:**
> I am having almost exactly the same problem.  I am using Ultimate Edition 2.5 which is Karmic 9.10 -- mine is 64 bit.  I have set the device to analog stereo output, and I have SB X-Fi Xtreme Audio CA0110-IBG listed as the device.  (Maybe the solution will be the same for both of us?)  My system is a dual-boot and the sound works in Windows 7 so I know the sound card is OK.


> **erixoltan said:**
> I just tried all the steps here:

[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

The steps worked (I had to use sudo bash instead of su) but no sound in my case.  Apparently this has worked for others. 	

I've also dual-booted with Windows 7, and it works there. And I followed those steps before and the steps mentioned here [http://ubuntuforums.org/showthread.php?t=1063987](http://ubuntuforums.org/showthread.php?t=1063987) and still nothing.

I hope there is a fix because I still need to use Windows 7 at this point for most things on my computer.

---

### Post by erixoltan on 2009-12-19
I went to opensourcesound.com and tried the steps listed there from 4Front Technologies.  I printed out the PDF (only needed the page with Linux instructions) and was able to get their instructions to work.  I had removed a lot of ALSA packages as shown somewhere to get rid of ALSA prior to trying OSS.  Then I went through the steps on the site -- it says dpkg -I but it means dpkg -i, other than that the steps worked.  I had to make sure to get the linux kernel source and other pre-requisite steps mentioned in the PDF.  

I was able to use osstest to produce the test sound that way.  (Sounded pretty good.)  

HOWEVER my applications don't know how to produce any actual sound.  Maybe they're hard-wired to ALSA or maybe the OSS doesn't truly work.  I can run sudo soundon and sudo soundoff with no apparent effect.  

Feel I'm making progress but not there yet.

---

### Post by erixoltan on 2009-12-22
I just solved my problem by removing the Xtreme Audio card and using the onboard sound.  It sounds perfectly fine, and when I reformat my hard drive and remove Windows 7, the new Ubuntu installation picks it right up.  

I am happy and no more Windows.

---

