---
title: "Best sound cards with support in Linux? S/PDIF and Analoge RCA outs at same time?"
date: 2010-01-27
forum: Hardware
---

### Post by BastardNamban on 2010-01-27
Using Ubuntu 8.04- I've finally settled back home after 5 or so years of wandering around between Japan and the USA, and I've dug out my amazing computer speakers- I have both a 2.1 Klipsch GMX Promedia set with analogue RCA inputs and a GMX D-5.1 with both RCA & digital S/PDIF inputs.

The last time I used both, I wired them to work together- I got a cheap 25$ or so PCI soundcard that handled simultaneous out for both digital and analogue signals, and hooked up both sets to work together- effectively a 7.2 surround set (ok, well, more like a 5.1 and 2.1 working separate, but it sounded AMAZING).

That was in my Windows days, on an old tower desktop. My main computer, and what I converted to pure Ubuntu use, is my Dell 9300 widescreen laptop. I started looking for an external PCI enclosure to use the old card from the desktop with my laptop, and realized there is no such thing (that I could find, or probably even affordable if there is one). I started looking at new soundcards, stuff like the HT Omega Claro Halo XT, the Auzentech X-Fi Forte 7.1, and the Asus Xonar Essence STX.

Problem is, all of those are internal cards. And very expensive.

I am willing to spend some money on something good, but I don't have a huge lossless music collection. Most FLACs I have are 20GB or so of Richard D. James' work (Aphex Twin, etc). In all my worried reading it seems a good soundcard will only make my mp3s sound WORSE. I know mp3s are lossy, and I know good sound when I hear it, so I'm thinking of getting serious anyway.

I'm looking for a recommendation- I want to simultaneously use the 5.1 and 2.1 sets- the 2.1 set as analogue, and the 5.1 through the digital S/PDIF connection like before, except now in LINUX, not windows, with great overall performance.... I've read some things to the effect that certain cards are better for gaming and some only for lossless sound....

Can anyone help me, without going into an audiophile's rant about the nuances of EFI shielding (unless you can make sense of what you're telling me)?? I need real help here.

Thanks for anything you can provide, sound cards have always confused me, but I've heard the difference they can make, and I want to learn.:D

---

### Post by BastardNamban on 2010-01-28
Really? No one? I've checked the ALSA compatibility list, and many high end cards are supported- including many I mentioned.

Is there no one there that has any personal sugguestions for my setup? Anyone running anything higher end that they recommend?

---

### Post by kaerumy on 2010-02-18
The Xonar STX Essence will not work on Ubuntu 8.04 out of the box, you'll have to compile the latest version of ALSA ([http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)).

It will work out of the box on Ubuntu 9.10 (Karmic) and sounds great via analog line out (RCA) and built-in headphone amp.

---

