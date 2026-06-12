---
title: "Lenovo S10-3s headphone socket non-functional"
date: 2011-01-05
forum: Hardware
---

### Post by DieseL1988 on 2011-01-05
I have recently installed Ubuntu 32-bit 10.10 on a brand new Lenovo S10-3s.

Most things work, with a few issues and available workarounds until future support improves - primarily wireless support.

However, there appears to be an issue with the sound card configuration. The Lenovo has a headphone port as most laptops/netbooks do. When plugging in headphones Ubuntu appears to fail to recognize this and does not mute on-board sound and fails to play sound via the headphones.

Also, the Lenovo S10-3s has an onboard microphone as well as a microphone jack. Neither appear to be recognised. I understand this is a common issue with Ubuntu on Netbooks.

---

### Post by DieseL1988 on 2011-01-05
Problem solved!

Add the following to the end of /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=thinkpad
```

Reboot and all is solved. Headphones work when plugged in and speakers are muted as expected. Also, the microphone can be unmuted in 'Sound preferences' and works perfectly.

This problem seems to be down to Ubuntu not detecting hardware correctly on install as with many other small issues on the Lenovo S10-3s. Hopefully it will be resolved in the next release.

---

