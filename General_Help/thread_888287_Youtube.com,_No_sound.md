---
title: "Youtube.com, No sound?"
date: 2008-08-13
forum: General Help
---

### Post by mysterio2004173 on 2008-08-13
I could play music fine, but youtube seems to be on mute. Please help!

---

### Post by maxmanapple on 2008-08-13
What version of Firefox are you using?

---

### Post by noobuntu35 on 2008-08-13
I run into this once and a while. Alien Arena wont play if Amorok is open, Check that no other audio programs are using the card. I usually close Firefox then re-open it when youtube has no sound

---

### Post by Rainstride on 2008-08-13
close you music app and wait 10 seconds and then open firefox try again.mine does the same thing.

---

### Post by maxmanapple on 2008-08-13
> **noobuntu35 said:**
> I run into this once and a while. Alien Arena wont play if Amorok is open, Check that no other audio programs are using the card. I usually close Firefox then re-open it when youtube has no sound

If that doesn't work, try updating Firefox to version 3, and get the latest flash/shockwave plugins because youtube's videos are FLV (what allows the mini player on the bottom) and some problems will appear if those aren't installed. This solved my problem and the totem one (my ToTem player was muted too).

Hope it helps...

---

### Post by Rainstride on 2008-08-13
> **maxmanapple said:**
> If that doesn't work, try updating Firefox to version 3, and get the latest flash/shockwave plugins because youtube's videos are FLV (what allows the mini player on the bottom) and some problems will appear if those aren't installed

the problem is caused by pulesaudio. i hear there gonna fix it in 8.10

---

### Post by mb_webguy on 2008-08-13
The current version of Flash has compatibility issues with PulseAudio.  Installing the libflashsupport package should fix the problem.  

Alternatively, you can install the newest Flash plugin, which will be included in Intrepid Ibex.  You can get the deb package [here]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree").

---

### Post by mysterio2004173 on 2008-08-13
Hmm.. I restarted my computer because it froze and youtube seems to work fine now.. but ubuntu freezes alot.. is there a way of fixing this?

---

### Post by noobuntu35 on 2008-08-13
> **mysterio2004173 said:**
> Hmm.. I restarted my computer because it froze and youtube seems to work fine now.. but ubuntu freezes alot.. is there a way of fixing this?

Reduce the amount of programs you are running at once or try an update a lot of that depends on system lay out CPU,Memory, and HDD speed read write cas latency etc.

---

### Post by Rainstride on 2008-08-13
> **mb_webguy said:**
> The current version of Flash has compatibility issues with PulseAudio.  Installing the libflashsupport package should fix the problem.  

Alternatively, you can install the newest Flash plugin, which will be included in Intrepid Ibex.  You can get the deb package [here]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree").

THANK YOU! your the first one iv seen mention this, it works perfect, i can finally listen to my music well on youtube!:guitar:\\:D/

---

### Post by KWM987 on 2008-08-13
> **mysterio2004173 said:**
> Hmm.. I restarted my computer because it froze and youtube seems to work fine now.. but ubuntu freezes alot.. is there a way of fixing this?

Reduce the amount of running processes, increase the amount of available RAM and swap space, if you don't have alot of custom configs or many files, you can do a reinstall of Ubuntu, since it goes pretty quick.

---

