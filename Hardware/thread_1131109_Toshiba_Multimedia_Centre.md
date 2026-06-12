---
title: "Toshiba Multimedia Centre"
date: 2009-04-20
forum: Hardware
---

### Post by at465 on 2009-04-20
Hi,

I recently bought a Toshiba Multimedia Centre, a USB soundcard/hub/ethernet device. It's no longer supported by Toshiba, but since it cost me only £8, I decided to give it a try.

It only has a mono PCM using the OSS sound device, and the ALSA one reports "Could not open audio device for playback".

I've tried it on Ubuntu 8.10, and the RC of Ubuntu 9.04, but does not work.

Googling, I found it's basically the same hardware as a Sound Blaster Live external, but not found any articles on that either.

Has anyone managed to get this working?

---

### Post by jarek.uk on 2009-05-26
> **at465 said:**
> Hi,

I recently bought a Toshiba Multimedia Centre, a USB soundcard/hub/ethernet device. It's no longer supported by Toshiba, but since it cost me only £8, I decided to give it a try.

It only has a mono PCM using the OSS sound device, and the ALSA one reports "Could not open audio device for playback".

I've tried it on Ubuntu 8.10, and the RC of Ubuntu 9.04, but does not work.

Googling, I found it's basically the same hardware as a Sound Blaster Live external, but not found any articles on that either.

Has anyone managed to get this working?

I've got it as well couple of weeks ago. I got it to sort of work on Ubuntu 9.04 using OSS.
By "sort of" I mean I can play music through it, i didn't have time to play around more with it. I'm pretty sure it wasn't mono, but i won't have a bet on that, as I tested it only for a day. I used spdif cable to connect it to my amp and sound was good.
Did you get anywhere with it?

---

### Post by at465 on 2009-05-26
No, sorry, I gave up and sold it to someone who still uses XP.

My speakers only have analog output. It could be possible that the digital supports stereo, but looking at the mixer it didn't look like it.

It's a shame they discontinued it, it seems a great fusion of different devices. I'm now using another usb sound card on a usb hub, but it's nowhere near as ideal solution as it all being integrated.

---

### Post by jarek.uk on 2009-05-27
> **at465 said:**
> No, sorry, I gave up and sold it to someone who still uses XP.

My speakers only have analog output. It could be possible that the digital supports stereo, but looking at the mixer it didn't look like it.

It's a shame they discontinued it, it seems a great fusion of different devices. I'm now using another usb sound card on a usb hub, but it's nowhere near as ideal solution as it all being integrated.

I found on a polish Ubuntu forum that it works great with pulseaudio. I didn't try it yet though.

If I'll get it to work, I'll translate solution as I think it's a great device (I want to use it with nslu2 and mpd).

---

