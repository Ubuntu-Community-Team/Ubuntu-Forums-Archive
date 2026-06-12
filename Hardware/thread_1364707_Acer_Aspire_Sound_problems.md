---
title: "Acer Aspire Sound problems"
date: 2009-12-26
forum: Hardware
---

### Post by Dada Maheshvarananda on 2009-12-26
Dear Ubuntu friends,

I have 2 sound problems with my Acer Aspire 4710-2009. I have Ubuntu 9.10.

1) When I plug in headphones, the external speakers do not turn off, so I cannot listen in privacy.

2) Neither the headphone microphone, nor the laptop's built-in micrphone pick up any sound.

I would be grateful for any advice how to solve these problems.

---

### Post by nmyrick on 2009-12-27
I am having the same problem with my built in microphone.  When I had Ubuntu 9.04 it worked, but now with 9.10, it does not.  Any help?  I have an Acer Aspire 4720z.

---

### Post by tuggy on 2010-01-01
bump

---

### Post by Dada Maheshvarananda on 2010-01-04
This solved the problem:

1) In terminal,
gksudo gedit /etc/modprobe.d/alsa-base
[enter password]

2) This opens alsa-base (/etc/modprobe.d) - gedit

(the page is blank)

Paste in: options snd-hda-intel model=acer

3) Save, close file, close terminal, restart computer.

---

### Post by nmyrick on 2010-01-05
Thanks Dada, I tried what you said, but mine still doesn't work.

---

