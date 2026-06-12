---
title: "NVIDIA Geforce 8600 GT"
date: 2015-08-29
forum: Hardware
---

### Post by Richard Menke on 2015-08-29
Hi there,

I'm stuck with a problem with a NVIDIA Geforce 8600 GT. I can not get the sound working with my HDMI output.

When i use lspci the video card is there, but the hdmi audio device is not there.

---

### Post by mikewhatever on 2015-08-29
Not all Nvidia cards have hdmi sound. ...not much to do about it.

---

### Post by blm-ubunet on 2015-08-29
Some of the early HDMI/DVI output cards can use the onboard mobo sound codec via spdif cable.
This limits the HDMI/DVI audio to spdif (2 ch stereo or AC3/DTS bitstream passthru').

Does your video card have spdif input header (4? pin SIL) ?

---

### Post by Vladlenin5000 on 2015-08-29
AS above, the S/PDIF connection is your only chance.
HDMI audio support in Nvidia started in the 9000 series.

Consider replacing it. It's a very very old card.

---

