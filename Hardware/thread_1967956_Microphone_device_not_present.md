---
title: "Microphone device not present"
date: 2012-04-28
forum: Hardware
---

### Post by rfictus on 2012-04-28
My microphone is not functioning in Ubuntu 12.04 'Precise'; is neither detected. 

Under the input tab under sound configure, no device is present hence nothing is selectable or adjustable. Was working fine in 11.10.

Basically, microphone device is not working anymore. Here is a screenshot: [http://imgur.com/NzTmv](http://imgur.com/NzTmv)

Any quick way to sort this out ??

---

### Post by rfictus on 2012-05-01
Right so I get this one fixed for the Vaio CW series.

Added this bit of code:

options snd-hda-intel model=toshiba-s06

to: sudo gedit /etc/modprobe.d/alsa-base.conf

I know, it says toshiba..

:popcorn:

---

