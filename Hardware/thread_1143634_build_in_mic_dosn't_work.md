---
title: "build in mic dosn't work"
date: 2009-04-30
forum: Hardware
---

### Post by verby on 2009-04-30
can you suggest something?
acer 5520, everything works including webcam (crystal eye) out of the box, except the build in mic. 
In volume properties, options I have choose internal mic there is no front mic options... any ideas, how to get it to work.

---

### Post by K. Hendrik on 2009-04-30
I`ve got the same Problem with my Acer Aspire 6935, so I hope some one is able to solve this.

---

### Post by verby on 2009-04-30
bump

---

### Post by RealG187 on 2009-04-30
Sometimes you have to play around with the audio settings. Goto system --> preferences --> sound and try switching input devices.

---

### Post by K. Hendrik on 2009-05-01
No it`s not just about playing with the audio settings, any other ideas or solutions

---

### Post by verby on 2009-05-01
is there a driver to download for this?

---

### Post by K. Hendrik on 2009-05-04
I forgot about this earlier my sound didn't work out of the box i had to add a line in /etc/modprobe.d/alsa-base.conf I added 
```

options snd-hda-intel model=auto

```

whitout this I have absolutely no sound but the mic does still not work.

---

### Post by cabez0n on 2009-05-12
Actually there is also an Acer model
```
options snd-hda-intel model=acer
```

But I still didn't find any way to get the internal mic working. Everything else works all right.

---

### Post by Macchi on 2009-05-12
Sorry I do not have a solution, but I have seen recently several reports of problems regarding built-in microphones, specially on notebooks. 

Apparently there is some problem (regression) in the kernel. Besides the fact that equipment manufacturers neither comply to standard ways of using the sound hardware nor provide ay information on their implementation tweaks. Thus our heroes working with kernel development have to reverse engineer settings on other operating systems in order to develop Linux drivers. 

PS: Personally I have been affected since we cannot use Skype on both of our EEE netbooks in the family, that obviously are now running Ubuntu 9.04.

---

### Post by Carl Hamlin on 2009-05-12
I got mine working on my Acer Extensa 5620 by swapping everything over to PulseAudio instead of Alsa. However, there's a hell of a lot of white noise in the background...

---

### Post by cabez0n on 2009-05-12
Oh yeah ? That's cool. But, is it usable the mic ? Say for skype and voice recording ?

---

### Post by Carl Hamlin on 2009-05-12
> **cabez0n said:**
> Oh yeah ? That's cool. But, is it usable the mic ? Say for skype and voice recording ?

Yes. I use it with Ekiga Softphone and Cheese. Lots of hiss, however.

---

### Post by verby on 2009-05-23
got a new Acer Aspire 4736, everything works nice, except... build in mic.
I use a Skype a lot and any help how to set it up would be appreciated.

---

### Post by verby on 2009-06-01
any idea?

> **verby said:**
> got a new Acer Aspire 4736, everything works nice, except... build in mic.
I use a Skype a lot and any help how to set it up would be appreciated.

---

### Post by guushoekman on 2009-09-26
> **verby said:**
> got a new Acer Aspire 4736, everything works nice, except... build in mic.
I use a Skype a lot and any help how to set it up would be appreciated.

I have the same laptop and same problem. Have you found a solution yet? Or does anyone know one?

---

### Post by cabez0n on 2009-09-27
New ALSA drivers make the mic work. 

Download and compile newest alsa ;-)

---

### Post by guushoekman on 2009-09-30
> **cabez0n said:**
> New ALSA drivers make the mic work. 

Download and compile newest alsa ;-)

Sweet!
I'll wait for Karmic Koala for the newest ALSA, but good to know the microphone will work.

Thanks for letting me know :)

---

### Post by richardh on 2009-10-05
i had the same problem with my new Samsung x460
finally discovered that there are TWO microphone inputs the way Ubuntu got set up on my machine.
- click on speaker icon (top right), 
- click on 'volume control' button
- click on 'options' tab
- on Input Source select (in my case) 'Front Mic' (may be some other input option listed)

if insufficient number of 'Input Source' on options page, click on Preferences button and select more input sources.

Hope this helps

---

### Post by john1066 on 2009-12-12
Re the following 

**** I forgot about this earlier my sound didn't work out of the box i had to add a line in /etc/modprobe.d/alsa-base.conf I added 
 	Code:
 	options snd-hda-intel model=auto 
whitout this I have absolutely no sound but the mic does still not work.****


I am also having acer webcam problems and I am new to Ubuntu. Could you give me more detail on what I use to add in this line?

Thanks,
John

---

