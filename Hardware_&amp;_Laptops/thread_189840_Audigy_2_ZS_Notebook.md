---
title: "Audigy 2 ZS Notebook"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by cam_tram on 2006-06-05
Hey, I'm thinking of getting an Audigy 2 ZS PCMCIA soundcard.  Is this compatible with Dapper, and if so is it hard to configure or have any major issues?

---

### Post by .t. on 2006-06-05
I have this card. There are two issues, but apart from that it runs perfectly (better than in Windows); it upmixes everything to 8-channel, but you knew that. Here are the issues.

1. The emu10k1 driver does not support hotplug. That means that once it's in, if you unplug it while the system's on, the kernel will crash. I've filed a bug at SourceForge, but there's not much activity.
2. Because of 1, Suspend and Hibernate do not work when the card is in.

Nonetheless, I manage to live with both those bugs, major though they are.

---

### Post by mihai.ile on 2006-06-05
also have one and works good, you don't have all things that comes from windows drivers but the sound is clear and optical out is working just fine, i didn't really test 5.1 and all this stuff if it really works how is supposed to be....
Also have those problems but i never take the cad out with the system running so....

---

### Post by it.henrik on 2006-07-31
does this cards input work?

According to this page ..

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs)

it does not.

can someone confirm?

---

### Post by cam_tram on 2006-08-21
Is there a way to safely "unmount" it while the computer is on without crashing the kernel?

---

### Post by .t. on 2006-08-21
Well, the fix was included in both the Dapper and Edgy kernels a couple of weeks ago, so you can unplug the card safely. However, to re-insert it properly, you will need to close all applications using the module, remove the modules (snd_emu10k1 and snd_emu10k1_synth), and then you can plug in the card so it'll be recognised and installed properly.

---

### Post by kandd on 2006-10-05
Hi,
i have an Audigy 2 ZS Notebook PCMCIA on Dapper. But the sound input doe NOT work. Can someone help me?!

---

### Post by radiance on 2006-10-15
Are there anyone who tried audig2 zs notebook in ubuntu and reached 5.1 sound?
I need to find out how to
I have one of this card and i want to make it work with ubuntu 
please help me..

---

### Post by .t. on 2006-10-15
radiance: It always works for me. I just plug it in, and I've got 7.1 sound!
kandd: Sorry, I've never tried input.

---

