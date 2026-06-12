---
title: "Realtek ALC263 - no sound from the right speaker"
date: 2018-05-22
forum: Hardware
---

### Post by bogzal on 2018-05-22
I have a sound issue on my **Lenovo V110-15IAP** laptop, equipped with **Intel HDA Audio / Realtek ALC263** codec and **Ubuntu 18.04**.

When using built-in speakers I get no sound from the right channel, and the left channel sound seems to come from the right speaker.

When using headphones everything works just fine.

I have googled a lot: I have checked settings/channel volumes in both pavucontrol and alsamixer. I have tried adding more-or-less random options to /etc/modprobe.d/alsa-base.conf (eg. options snd-hda-intel model=basic). But it did not resolve the issue.

Here is my ALSA Information log: [http://www.alsa-project.org/db/?f=dabcf66c76a74eba7e2fa84be5d0b17700c703d3](http://www.alsa-project.org/db/?f=dabcf66c76a74eba7e2fa84be5d0b17700c703d3)

Any suggestions/help would be greatly appreciated.

Bog Zal

---

