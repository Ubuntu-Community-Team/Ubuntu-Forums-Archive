---
title: "Creative Soundcard - No Sound!"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by rich.bradshaw on 2006-12-21
Hi,

When I booted up Live-CD my soundcard worked fine. On install it doesn't work anymore.

I have turned up all volumes in alsamixer, lspci gives me:

```
$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

Sound in system/preferences/sound has everything set on auto-detect, and changing the default soundcard there from Intel ICH5 and CA0106 doesn't help....

Any ideas?

Thanks!

---

### Post by budgie9 on 2006-12-21
You seem to have two cards in the list, Is one the on board sound card and the other the SB? If so you may well hae a conflict, perhaps in the IRQs of the computer. You may need to disable the on-board card in the BIOS and then test again. It may be so that you have to disable the internal card via a jumper.  I have found with some m/boards the internal sound card holds an IRQ address even when supposedly disabled in the BIOS. Check with your m/board manual.

---

### Post by rich.bradshaw on 2006-12-22
I am not sure what the Intel one is - I assume it's an internal one. I have had it working out of the box with many other distros, and it did work with the live-cd, so I am sure there is an easier fix. My awesome Dell bios won't let me disable onboard either... ](*,)

---

### Post by szf on 2006-12-22
I have the same sound card. You've already stated that you checked System -> Preferences -> Sound. That the devices tab was set for 'Autodetect'. Is the sounds tab set to use device CA0106?

Also, if you open up the volume control applet (right click the speaker), it should be set to device CA0106 tracking Analog Front.

---

### Post by rich.bradshaw on 2006-12-22
Aha, I can disable on board sound - still doesn't work though -  I have it set to use CA0106 now, with things on first tab set to autodetect. I have Analog front enabled with full volume - still nothing..

---

### Post by rich.bradshaw on 2006-12-22
any ideas?

---

### Post by budgie9 on 2006-12-22
This may be the obvious thing, but let's check you have done it.
Have you checked the audio settings under the volume control  Right click on it in the top of your screen and select the options.
Now make sure your card is selected and the devices shown are not disabled, by having a red cross on them.  Sorry I can't be more detailed at this point as I am in  XP.
At least two tabs will be showing Capture is one, that is for the mic, but take a look anyway and make sure all is as it should be.

---

### Post by szf on 2006-12-22
Yurgg. The tests (System -> Preferences -> Sound; Devices tab) don't do a thing? 

Is Analog Center/LFE also active via the sound applet? Sorry if I'm grasping a straws, but I twiddled things under Edgy for the Significant Better Half (SBH) post-installation `til sound came back for both logins.

---

### Post by rich.bradshaw on 2006-12-27
Yeah all volumes are on and up etc...

---

### Post by budgie9 on 2006-12-27
I am unable to help you further at this stage. Perhaps you have hit a bug in Edgy, as some others seem to see also.

This page may give you some other options to try. 
[http://www.faqs.org/docs/Linux-HOWTO/Sound-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Sound-HOWTO.html)

---

