---
title: "Sound problems"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by mario8723 on 2005-03-11
This may sound silly, but my soundcard isn't working and I can't figure out what the problem may be. I haven't thought much of it since installation about a week or so ago, only because I knew I had bad speakers that needed replacing. However, I just got new ones and I still have no sound.

Do I have to setup my soundcard (VIA VT1720 Evny 24PT Chip ( 8 Channel Audio) Onboard) and, if so, how do I go about it? I've already tried in the system menu but that doesn't seem to working at all....

Any help would be greatly appreciated.

---

### Post by mario8723 on 2005-03-12
Anybody? :sad:  :sad:

---

### Post by bored2k on 2005-03-12
[QUOTE=mario8723]Anybody? :sad:  :sad:[/QUOTE]
 Do you get a sound when Display Manager appears ? [like  a bump]
Did you try changing inputs in gstreamer-properties ?

---

### Post by mario8723 on 2005-03-12
I get no sound, and yes I did try configuring gstreamer-properties...

When I test any of them I get:
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'
Failed to construct test pipeline for 'OSS - Open Sound System'

Any suggestions?

---

### Post by mario8723 on 2005-03-13
Can anybody help me? It's a VIA onboard sound chip and it doesn't seem to want to setup with alsa...

---

### Post by trigg on 2005-03-13
[QUOTE=mario8723]Can anybody help me? It's a VIA onboard sound chip and it doesn't seem to want to setup with alsa...[/QUOTE]

what version of the distribution are you using? Hoary? Warty?

What is your lspci and lsmod output?

What version of alsa do you have installed?

Let's try and diagnose before throwing out random solution attempts.

trigg

---

