---
title: "No Sound on AD1986A After Ubuntu 11.10 Install"
date: 2012-08-11
forum: Hardware
---

### Post by exit2600x on 2012-08-11
I installed Mythbuntu 11.10 and ran updates. I get no sound at all. I have a Asus M2NPV-VM motherboard with the Analog Devices AD1986A onboard sound card. Sound worked from the install cd, but after install, no sound. I ran:

cat /proc/asound/card0/codec* | grep Codec
Codec: Analog Devices AD1986A

I've tried changing the audio device under system/preferances/volume control to what looks like the correct audio device. I've also tried the other ones listed. None of them work. I have tried muting and unmuting in alsamixer.

Can anyone help?

---

