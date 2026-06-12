---
title: "No sound through ALC888 for HP a6010n"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by dancingbuffalo on 2009-07-17
Hey,
I recently installed Ubuntu 9.04 recently.  It all seems well except I have no sound at all (except the whir of my fans and dvd drive).  I've checked some of the suggestions, but most seem to be when you have minimal sound (where as I have absolutely none).  I went through all of the steps of [http://ubuntuforums.org/showthread.php?t=205449&highlight=hp+alc888](http://ubuntuforums.org/showthread.php?t=205449&highlight=hp+alc888) and it seems like the drivers are loaded.  I've even tried the ALSA driver compilation method they recommend.  I get through all of the steps without incident, but when I am referred back to Step 4 of the General Help section where I enter "sudo modprobe snd-hda-intel" and it doesn't appear to do anything.  I type "lspci -v" and see my driver, which is good, but I still get no sound.  I've gotten into alsamixer and nothing seems to be muted.

A little side information: my system is set as dual bootable between Linux and 32 bit Vista Home Premium.  I can get basic stereo sound when in Vista (still trying to remember how I got it through the S/PDIF before, but that's a thread for a different forum).  It is an HP a6010n with a Realtek ALC888 audio processor.  It looks like it should be ALSA compatible with the hda-intel module.

Any suggestions?  While I have a fair idea of what I'm doing, I'm still pretty new and can get easily lost.  Thanks in advance.

---

### Post by dancingbuffalo on 2009-08-16
I kinda found a solution.  I went out and bought an Asus Xonar D1 sound card.  Works wonderfully.  Jaunty (64bit) recognized it right away.  Once I figured out how how to unmute IEC958 sound came through the digital audio (fiber optic) output without problem.  Highly recommended.  Btw, it also works in Windows Vista 32bit without incident, but again you have to enable the digital out.

---

### Post by Stupendous man on 2009-08-16
WHAT??

Well that just grinds my gears, because I have a Xonar D1 and can't get jack squat out of it except for in Totem...

I love/hate Ubuntu.

I don't suppose you could give a beginner some instruction on how to get it to work like yours does? I have it connected to a Yamaha receiver via an optical digital cable via the s/pdif output... but nothing I do will allow the sound to come out during games or anything online.. Also no OS sounds either, like startups and "dings" or whatnot...

---

### Post by dancingbuffalo on 2009-08-16
Umm...I'm not really sure (I'm kinda new too).  I just kinda plugged it in and heard it going.  I just had to mess around to get the digital out going.  It sounds silly, but I expected trouble with the digital out so I used the chintzy 1/8" to RCA connections and trouble shot that.  Big thing is to just make sure that you're on the right input mode.  Even if the sound card's outputting right, if the recievers looking in the wrong spot, not much is going to happen.

Once you get basic sound out of it, get into the alsamixer.  On the basic install of Jaunty, you can get to one through Terminal (Applications>Accessories>Terminal).  From Terminal type "alsamixer" (minus quotes).  You'll get some retro looking bars on the screen.  Press the right / left keys until you find IEC958 and press "m".  This will unmute the digital out and change the little box above IEC958 from MM to something else (mine just says 00).

Go back to your sound reciever and change the input to whatever it calls the fiber optic in and play some music or something.

Hopefully, this works.

---

### Post by Stupendous man on 2009-08-17
> **dancingbuffalo said:**
> 

Hopefully, this works.


Dude, I owe you a beer ;)
Sound works in all applications now. Now all I have to do is figure out why the surround channels aren't active, and it will be perfect.

Thanks man.

---

