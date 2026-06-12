---
title: "Sound only over Headphones"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by dex80 on 2005-06-13
hi,

on my laptop i only hear sound over headphones but not over the speakers.

under windows xp i normally hear sound over the speakers and when i
insert headphones i hear the sound only over the headphones.

but under kubuntu the speakers do not work.

any ideas?

i already  have spend tens of hours the last week with google to find solutions
for my problems. this is one of 5. i have given up to search in google. maybe
someone here can help me. i am really out of energy to search.
it took me one week to find out how to get my wifi  running with ndiswrapper and
to find out that acpi is mayking my clock running 2x to fast and  that a new kernel solves my dma=off problem of my hd. there are still other problems.

i hope someone can help me here with the sound problem.  :???:

Running: kubuntu hoary. kernel 2.6.10-5-386

---

### Post by venni on 2005-06-14
I had similar problem. Here's what I had to do..

Open KMix and go to Switches tab. Then make sure that the External Amplifier is selected by clicking on the dot above it. This did the trick for me.

Hope this helps,

-venni

---

### Post by dex80 on 2005-06-14
i tried this but it does not help. :/
have tried some of the buttons on/off here and there but
nothing helped.

---

### Post by dex80 on 2005-06-16
hi,

i have just installed debian testing distribution.

there i have sound over the main speakers.

how can if find out the difference between ubuntu and debian configuration?

---

### Post by dex80 on 2005-06-16
ups.

i hear something but the main speakers are used as beepers.
playing an mp3 does still not work over the main output

---

### Post by edu65 on 2006-10-28
This is most strange. I had the same problem after going through the usual updates and switching to the 686 kernel in order to get SMP support.

I rebooted using the 386 kernel and got sound from the built-in speakers (just like
after a fresh install).

Now the strange part... booting back to the 686 kernel has made the speakers work again!  

Sorry if this does not help anyone. I just wanted to share my experience...

Using Dapper with a 2.6.15-27 kernel (HDA Intel / alsa mixer) on a Dell Inspiron 6400.


> **dex80 said:**
> hi,

on my laptop i only hear sound over headphones but not over the speakers.

under windows xp i normally hear sound over the speakers and when i
insert headphones i hear the sound only over the headphones.

but under kubuntu the speakers do not work.

any ideas?

Running: kubuntu hoary. kernel 2.6.10-5-386

---

