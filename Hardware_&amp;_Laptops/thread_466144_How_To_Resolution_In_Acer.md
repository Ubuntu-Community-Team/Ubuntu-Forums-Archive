---
title: "How To Resolution In Acer"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by black_ice on 2007-06-06
hello all ..,

and thanx for this great forums ...,

i have feisty on my laptop acer aspire 5601 with vga card intel graphics media accelerator 950 and the screen is WXGA and i cannot edit the resolution 1024 * 768 i have tried to edit in the /etc/X11/xor.conf but it made me to reinstalled the ubuntu for 3 times :S


Any one has asolution for this problem

---

### Post by srt4play on 2007-06-06
I'm going to take a wild guess and say you're shooting for a resolution of 1280x800.  One option is to install the package xserver-xorg-video-intel in Synaptic but that may prevent proper suspend and resume on your laptop.

Probably the better way is to install the package 915resolution in Synaptic and use it to get your desired resolution.

---

