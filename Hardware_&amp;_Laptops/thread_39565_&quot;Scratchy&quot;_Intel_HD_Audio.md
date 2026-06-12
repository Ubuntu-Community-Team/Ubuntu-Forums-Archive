---
title: "&quot;Scratchy&quot; Intel HD Audio"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by Varanger on 2005-06-05
hello all!

I recently bought a new computer and I am some problems with Linux ever since.

First, I couldn't make Audio work.

I ran "lspci | grep -i audio" to find out which was my audio card 

The output was:

0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

Reading every article I could have foun on the net regarding this card, ubuntu and Linux, I discovered that i needed snd-azx (ALSA 1.0.8 ) or snd-hda-intel modules (ALSA 1.0.9rc* or later).

Using Ubuntu official repositories (universe)

I ran "apt-get install alsa-source". Later I followed some steps for compiling the specific card drivers (snd-azx), then building the deb file and installing it with dpkg.

I could make audio work but it sounded "Scratchy"

Following the steps from here: [http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto)

I downloaded the lastest files from [www.alsa-project.org](www.alsa-project.org) to build and install ALSA 1.0.9 (1.0.9 release not the release candidates) and lately 1.0.9a. As the link above said, the driver has changed from snd-azx to snd-hda-intel. After following all the steps and rebooting I am getting the same "scratchy" audio.

I've looked every on the net and haven't found anything to help me out!  ](*,) 

This Intel Hd Audio card is a integrated soundcard which came with the mainboard Intel D915GEV.

Thanks for the help,
Santiago

---

### Post by BerndM on 2005-06-26
I have the exact same problem with the exact same card!!! Also tried looking every where for some info on how to get it fixed. As a matter of fact that how I came to this thread to begin with!

It's awful Not one of my RHL distro's gives audio for this card, not my FreeBSD 5.4 gives me sound none of them.

Whoever said newer is better? I got sound on my old computer right away!  :mad:

---

