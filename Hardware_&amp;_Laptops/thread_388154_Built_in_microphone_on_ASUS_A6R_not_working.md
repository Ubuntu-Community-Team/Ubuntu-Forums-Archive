---
title: "Built in microphone on ASUS A6R not working"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by martinnorth on 2007-03-19
I've recently installed Edgy on my ASUS A6R laptop. After a lot of of work, just about everything is working fine, apart from the built in microphone. 

lspci shows:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

I've tried experimenting with various ALSA combinations, but without success. Under Sound --> Preferences, Sound Capture, if I select ATI IXP AC97, it generates the error:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

If I attempt to open Sound Recorder, I get:

Your audio capture settings are invalid. Please correct them in the Multimedia settings.

If I change the Sound Capture to OSS, the errors stop. I can use Sound Recorder, but when I play back, there is no signal.

Any suggestions? I'll post any additional information if needed.

---

### Post by hardyn on 2007-03-19
i have been wanting to try this... is your A6R the sister model of any of the System76 machienes? or is an A6r an older machine? if it is a sister model,.. try their deb... its available as a link from their web site.

good luck.

---

### Post by martinnorth on 2007-03-19
I've had a quick look at the System 76 site, but I don't think I'm going to be able determine whether the A6R has an equivalent.

---

