---
title: "using headphones on feisty"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by ravinsp on 2007-05-26
I have Ubuntu feisty on my Samsung NP R40 laptop. It's sound card is working properly on ubuntu.

The problem is when I attach a headphone ubuntu gives sounds from **both** the pc speaker and headphone.** I want Ubuntu to turn off the pc speaker when I plug a headphone.**

(I previously had a problem with the alsa configuration. I solved it by adding the line

[COLOR="DarkRed"]options snd-hda-intel probe_mask=8 model=auto[/COLOR]
to the file
[COLOR="DarkRed"]/etc/modprobe.d/alsa-base[/COLOR]

using [[COLOR="Red"]_**this thread**_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=433659"))

-RavinSP-

---

