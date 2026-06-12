---
title: "[artful] No sound on 7th gen i5 NUC over HDMI or Analog"
date: 2017-10-22
forum: Hardware
---

### Post by lexxonnet2 on 2017-10-22
Hello all,

I've just got my parents a 7th gen i5 Intel NUC, and have tried a bunch of different things to get sound to work (reliably) over either the HDMI output or the Analog output. However, I can't seem to get either to work particularly well. At times, it will randomly decide to work out of one of the ports, and seemingly work till the next reboot, but it doesn't seem to do it with any consistency.

Pulseaudio seems to recognise the hardware (and even recognise and switch to analog when I plug in an analog audio cable), and pavucontrol even shows that audio is being output, but nothing actually seems to come out.

Most of the threads I've read seem to point towards installing the alsa-daily dkms driver, which I've done. I've even gone back and installed a few older ones, but to no avail. I'm presently at my wits end and would appreciate any help on this!!

Cheers,
Abhinay

---

### Post by Autodave on 2017-10-22
Have you installed any video drivers? If so, what ones and where did you get them from?

HDMI should be hooked up *before *booting the machine. Hooking it up afterwards will usually cause it *not *to be recognized.

---

### Post by lexxonnet2 on 2017-10-22
I haven't installed any (I assume Ubuntu just ships with the standard intel video drivers and the video output is fine), and the HDMI is always hooked up.

---

### Post by lexxonnet2 on 2017-10-23
Okay, so I've just given up and started using the analog output. Turns out, the TV would recognise sound from the analog out when the computer was first booted up, but at some point switch and start expecting it from the HDMI. Problem temporarily solved by just connecting the analog output to some speakers. Hopefully, the HDMI output will be reliable in a future kernel update :)

---

