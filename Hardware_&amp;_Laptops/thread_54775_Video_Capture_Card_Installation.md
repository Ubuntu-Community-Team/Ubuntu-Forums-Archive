---
title: "Video Capture Card Installation"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by Refund on 2005-08-06
what do I need to do to install a video capture card?
(and what software will i need)

it's an old "pixelview" model (bt878 I think)

cheers in advance

---

### Post by chaumurky on 2005-08-10
[QUOTE=Refund]what do I need to do to install a video capture card?
(and what software will i need)

it's an old "pixelview" model (bt878 I think)

cheers in advance[/QUOTE]
 Not meaning to hijack but I have the same card and when I boot with the card in a slot an error message flies by over and over so fast I can't read it. Is this a hotplug thing? If so, can I disable the initial probe of this card so I can boot and go from there?

---

### Post by c-m on 2005-08-10
ignore me just subscribing to the thread since i have a WinTV-GO card that i need help setting up and think its the same bt878 chip?

---

### Post by chaumurky on 2005-08-11
Ah, what a tease. Oh well, anyone else?

---

### Post by Lunde on 2005-08-11
[QUOTE=Refund]what do I need to do to install a video capture card?
(and what software will i need)

it's an old "pixelview" model (bt878 I think)

cheers in advance[/QUOTE]
 A lot of the bt878 chipsets are supported by the bttv driver. you just need to start the module which is already in your kernel.

Find your card and tuner type in the link below, just scroll down to you see the list.
[http://www.alllinuxinfo.com/howto/show/BTTV.html](http://www.alllinuxinfo.com/howto/show/BTTV.html)

The only thing i needed to do with my bt878 was to put these lines in **/etc/modprobe.d/local**
```

alias char-major-81-* bttv
options bttv card=0x64 tuner=38

```
The above is for Hercules Smarttv2 stereo.

---

### Post by chaumurky on 2005-10-01
This is mine.

```
# card=37 - PixelView PlayTV pro
# tuner=5 Philips PAL_BG (FI1216 and compatibles)

alias char-major-81-0 bttv
alias char-major-81-1 off
alias char-major-81-2 off
alias char-major-81-3 off
alias char-major-81-64 radio

options bttv card=37 pll=1 radio=1 tuner=5

```

---

