---
title: "Howto Midi-Usb ?"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by Brasero on 2005-09-05
Is ther any information how to install midi-usb interface ?
I was searching  answers on german and french wiki to . But no answer to my question.
I'm using Novation Remote25  .
[B]
sudo lsusb -v [/B] says harware is detected.
But with alsa there is a problem , in actual release snd-usb-midi  seems have been included in snd-usb-audio. The device is not activated.
Even with adding:
[B]modprobe snd-seq-device
sudo modprobe snd-seq-midi[/B]

**pmidi -l** only shows my onboard devices

Has any body a solution to my make midi-usb  only work ?

---

### Post by Brasero on 2005-09-08
It seems very strange , i have no answer to midi usb device with Ubuntu.
I have made same kind of thread in 2 german and 1 french ubunto forum no answer to.
Would it mean that nobody was able to make working and usb-midi device with Ubunto ?

---

### Post by Smbrandes on 2008-01-09
Usb midi under gibbons appears to work without any intervention. How to offset two usb midi devices is another matter.

---

