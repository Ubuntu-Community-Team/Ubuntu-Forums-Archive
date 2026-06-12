---
title: "Front Mic Jack Problem"
date: 2009-08-01
forum: Hardware
---

### Post by QuickNinja on 2009-08-01
Hello Everyone,

I just encountered a problem with my new computer case.  When trying to use a microphone to see if it worked, I plugged it into the front microphone jack of my Antec 300 Gaming Case.  It didn't work.  The mic is part of a headset and it uses a 3.5mm mic plug and a 3.5mm sound plug.  Plugging the sound plug into the front sound jack of the case works, but using the mic plug in the front mic jack doesn't.  I opened my case and made sure the HD audio connector was properly secured to the motherboard, and it was connected.  I can take the mic 3.5mm jack and plug it into the back microphone jack that is apart of my mother board and it'll work fine. 

 What gives? :???: Is my case screwed up or is there some mysterious setting that I have to fix?

---

### Post by QuickNinja on 2009-08-01
Adding information

I am using Device: HDA ATI SB (Alsa Mixer) with Master, PCM, Front, Line-In, and Microphone on max volume.  When I blow in the mic when it's plugged into the front mic port, I can hear it.  So it's just some setting that I have to change, but I don't know what it is.

I can also use AC 97' audio plug if I need to as my case supports that as well, but I already have the HD audio plugged into the motherboard.

I'm also using a Gigabyte GA-MA790XT-UD4P MOTHERBOARD

---

### Post by QuickNinja on 2009-08-01
Never mind everybody I was able to figure out the problem by myself.

YEA!\\:D/

---

### Post by Revolutionary101 on 2009-08-14
> **QuickNinja said:**
> Never mind everybody I was able to figure out the problem by myself.

YEA!\\:D/

How did you fix it because I am having the same problem.

---

### Post by Mesqueeb on 2010-07-13
I was having the same problem but I was able to solve it:

Just go to Applications -> Sound & Video -> Gnome Alsa Mixer
and make sure the checkbox "Mic Front Input" is checked.

If your mic is live all the time, just check "mute" underneath the mic bar.

And always ensure that they got saved by "sudo alsactl store 0" in terminal.

Cheers!

---

