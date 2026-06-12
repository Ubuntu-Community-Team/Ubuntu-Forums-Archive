---
title: "Audio HDA-Intel Card..disappeared"
date: 2008-04-29
forum: Hardware
---

### Post by itfsos on 2008-04-29
hi guys..can I explain you a problem?

i've reinstalled Gutsy after some problems with my wireless card in Hardy..like the first time,i had a problem with the audio card: it usually works,but with an horrible whistle! So,like 6 months ago,I've installed newer alsa drivers(i used the same as the fisrt time in Gutsy),added the module in /etc/modules...and now my Audio Card is not recognized by the system!:( if i run "alsaconf" i can configure it,but then nothing happens and the system doesn't find it.

I also ran "lspci | grep 'audio'" but ubuntu didn't return nothing..
How can I try to get it work again? if you need some additional informations let me know..hope someone can help me!

P.S. I have an integrated Intel Sound Card.

P.P.S. Sorry for my awful english!:)

---

### Post by guruofquality on 2008-04-29
what does "dmesg | grep snd_" (w/o quotes) show?

If there is a bunch of errors, then you have the same problem as my sisters laptop.

The fix for me was to:

sudo rm -rf /var/cache/apt/*
sudo mkdir -p /var/cache/apt/archives/partial
sudo apt-get autoclean

then open synaptic package manager and choose reinstall for everything kernel  related and everything alsa related.

Sounds ridiculous, but it worked!

---

### Post by itfsos on 2008-04-30
it worked..thanks a lot!

now I've re-installed alsa drivers ad all is going ok..don't know why the first time failed!

Solved!:)

---

### Post by gavinm on 2008-05-01
Any suggestions on what might be wrong if "dmesg | grep snd_" does not report any errors at all, yet there is no sound from the HDA-Intel audio subsystem?

---

### Post by itfsos on 2008-05-01
the first thing I can imagine is...to UNmute volumes in alsamixer,but probably you have already done it!

---

