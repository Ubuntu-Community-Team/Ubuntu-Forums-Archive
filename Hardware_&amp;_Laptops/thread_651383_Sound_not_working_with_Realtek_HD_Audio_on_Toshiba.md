---
title: "Sound not working with Realtek HD Audio on Toshiba x200-20T"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by efikkan on 2007-12-27
Hi

I got a Toshiba X200-20T with a Realtek HD Audio sound card. I'm running 64bit Ubuntu 7.10.

Output from "lspci -v"
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


I can hear sounds in some(I think two of them) of my speakers(the laptop got five speakers), but there is no bass. The headphones are not working.

I've tried downloading the lates drivers from Realtek: realtek-linux-audiopack-4.07a, but I can't compile them. 

I've tried different methods from different forum threads, but none of them worked on my computer.

Can anyone please help?

Thanks.
Merry Christmas.

---

### Post by fazavon on 2007-12-27
A buddy of mine, has that same laptop and he has no sound.

It is something to do with Toshiba being... .well you know what I want to say. 

I can not find the website that had the specific reason, but it has something to do with the Chip set.

Sorry

//j

---

### Post by Digger78 on 2007-12-27
Have you tried editing /etc/modprobe.d/alsa-base

adding the following to the bottom of the file

```
options snd-hda-intel model=toshiba
```

then reboot

---

### Post by fazavon on 2007-12-27
We have tried that...

We even tried re complying the alsa drivers form scratch

---

### Post by efikkan on 2007-12-27
> **Digger78 said:**
> Have you tried editing /etc/modprobe.d/alsa-base

adding the following to the bottom of the file

```
options snd-hda-intel model=toshiba
```

then reboot Now the sound in the headphones works, but the switching between headphones and speakers does not work.

The bass speaker is still silent.

---

### Post by efikkan on 2007-12-29
Would it help if anyone else compiled the Realtek HD Audio drivers in 64bit for me? (create a deb-file?)

---

### Post by drad on 2008-01-27
I had the same problem with my laptop Toshiba Satellite A105 - 

I Added this line at the bottom of my /etc/modprobe.d/alsa-base
"options snd-hda-intel model=toshiba" without the "

and found no difference. Sound at about 30% of max, when all levels are up to 11.

However when I changed it to "options snd-hda-intel model=asus" I got sound.

Darn I lost the tutorial, as it is bookmarked on my laptop. :confused:

---

### Post by john3333 on 2008-01-28
I had a similar problem with my laptop Toshiba Satellite A200
What worked for me was to call it a lenovo, and add this line at the bottom of my /etc/modprobe.d/alsa-base

options snd-hda-intel model=lenovo

I know it sounds odd to pretend it's a lenovo instead of a toshiba, but this worked for me. The suggestion was in another thread about sound problems.

---

