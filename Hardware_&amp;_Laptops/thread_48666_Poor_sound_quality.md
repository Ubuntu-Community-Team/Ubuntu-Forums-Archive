---
title: "Poor sound quality"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by Android on 2005-07-13
I have recently installed Ubuntu on my laptop and everything seemed fine until I loaded up Rhythmbox and started to play some mp3's. The sound breaks up slightly and crackles as the volume of the song increases. Whilst this isn't awful, it is really annoying. I have tried different speakers and headphones with no luck. I have also tried XMMS to see if it was a software problem.Does anyone have ideas?

---

### Post by varunus on 2005-07-13
What sound card is in your laptop?  This may be a problem with the "esd" daemon using OSS...try installing "libesd-alsa0" from synaptic, and following the "Configure sound properly" section over at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) to get sound working...

I wrote the original howto that one is based off of, so I can help with your sound problems...just let me know what card you have.

Good luck.

---

### Post by lordgibbness on 2005-07-13
Try running alsamixer from the command line and turn everything to the minimum and  disable what you can. There are lots and lots of settings... scroll along to the right. Now use something like kmix to turn what you want up one by one. This fixed crappy sound I was getting when using my TV card.

---

### Post by DancingSun on 2005-07-13
The easiest "fix":

Keep the PCM volume in the sound properties panel at around 70-80%.  You can get there by double clicking the speaker icon in the gnome panel.

I have this exact same problem, and I use esd as the default gnome audiosink, with the source from ALSA sound driver.

I don't have access to libesd-alsa0 as I'm using Ubuntu AMD64.

Soundcard is an onboard RealTek ALC850 chip.

---

### Post by Android on 2005-07-14
[QUOTE=DancingSun]The easiest "fix":

Keep the PCM volume in the sound properties panel at around 70-80%.  You can get there by double clicking the speaker icon in the gnome panel.

I have this exact same problem, and I use esd as the default gnome audiosink, with the source from ALSA sound driver.

I don't have access to libesd-alsa0 as I'm using Ubuntu AMD64.

Soundcard is an onboard RealTek ALC850 chip.[/QUOTE]

Thanks for the help guys. I did everything you said and it seems to of fixed it. I think the volume was going to too loud and distorting. 
My sound chip is a SiS SI7012 intergrated thing, it's always been pretty rubbish, even in Windows.

---

