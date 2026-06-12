---
title: "TX1000 Headphone jack issue!"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by persian_x on 2008-03-18
I will have to start a new thread for my HP tx1000, since I've looked EVERYWHERE for a solution concerning my dual headphone jacks up front.

I've looked in every thread and followed peoples instructions but nothing has worked so far! I get sound from my speakers but nothing from headphones
this is what I have in /etc/modprob.d/alsa-base:
" options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0 "

in alsamixer I cant turn up/turn down the headphone it stays at 00,

I've tried installing latest stable alsa drivers but failed, no sound out of speakers nothing.

my sound card is  ALC861VD

Does anyone have a solution for this? I am MISERABLE, i cant even watch my pr0n peacefully anymore

---

### Post by Arthur Archnix on 2008-03-18
I heard that the "latest" alsa drivers are busted in buntu. Try the 15rc3 ones.

---

### Post by persian_x on 2008-03-18
I've tried RC3 too, but nothing

I specifically followed this guide : [http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound](http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound)

but it didnt help it caused me even more trouble, not having any sound for a whole week I had to roll back driver

---

### Post by persian_x on 2008-03-18
by the way, my mute button always stays ORANGE, no matter what

when I updated alsa driver to 15rc3 it turned blue but no sound nothing my soundcard wasn't even recognised

---

### Post by Arthur Archnix on 2008-03-18
Those instructions are bad. At a minimum, you should have used this:
```
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

```

Try these directions:[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

