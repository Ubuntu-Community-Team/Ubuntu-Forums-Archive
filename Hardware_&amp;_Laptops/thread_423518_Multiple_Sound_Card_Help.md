---
title: "Multiple Sound Card Help"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by itchanddino on 2007-04-25
At random, Feisty seems to randomly change the default sound card on me.  I have an onboard one and a Soundblaster Live.  I'll go to sound, select the hardware I want, but sometimes this will change every couple boots.  Is there a way to make Feisty ignore the onboard card completely?  Thanks!

Edit: Disabling the sound card in bios does not work (wtf!).  I still get sound out of the onboard for some odd reason.

---

### Post by itchanddino on 2007-05-08
I'm still occasionally getting this problem.  Does anyone know how to set up Feisty correctly with multiple sound cards?

---

### Post by LxP on 2007-05-08
> **itchanddino said:**
> At random, Feisty seems to randomly change the default sound card on me.  I have an onboard one and a Soundblaster Live.  I'll go to sound, select the hardware I want, but sometimes this will change every couple boots.

I am in the same situation.  I have an on-board sound card and an M-Audio Audiophile, but unlike you I want to be able to use the two cards independently (they are hooked up to different pieces of equipment).

Hopefully someone knows the solution... :)

---

### Post by DracoPsycho on 2007-05-08
Hi there. I also have 2 sound cards in my PC. One is some onboard card and the other is SB Live!. First of all you have to somehow check which module your onboard card uses. My was snd_via82xx. You can check which modules you're using with command 
```
lsmod
```
When you know which module is it you go to /etc/modprobe/blacklist and you type module's name in it. After reboot the module shouldn't be loaded, so there's only SB in system and it's always default.

I don't remember exact place where blacklist file is but it should be somewhere similar as I said.

---

### Post by itchanddino on 2007-05-10
Thanks, that worked like a charm!

---

### Post by DracoPsycho on 2007-05-10
That's great :)

---

