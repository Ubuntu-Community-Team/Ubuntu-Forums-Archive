---
title: "M-Audio Audiophile USB - broken digital output"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by closey on 2007-06-23
Hi guys,

I've recently bought an M-Audio Audiophile USB for use in Windows and Linux. This sound card has a stereo analog output, a stereo analog input, a SPDIF (coax) digital output and a SPDIF (coax) digital input along with a MIDI port.

Now to my problem - all the functions seem to work (although requiring a reset of the device from time to time) except for the digital output. This feature works in Windows XP without a problem. I can't seem to get it to work no matter what I use as the device_setup parameter to the snd-usb-audio module. I've already filed a bug at the alsa bug tracker here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3181](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3181)

I have a problem the maintainer for the usb driver bugs isn't too active these days... What I'm asking is if anyone else has had any luck with this device's digital output and if so, what version of ALSA were you using?

Thanks heaps :)

---

### Post by closey on 2007-06-24
I realise this post should probably be in the Multimedia/Video section - can someone move it please? Thanks.

---

### Post by closey on 2007-06-25
Well, I managed to find that the problem is not with the drivers but some device incompatibility. The Pioneer DJM-800 simply doesn't like the signal sent from the M-Audio Audiophile USB. If anyone else has used this setup successfully, let me know please.

Thanks :)

---

