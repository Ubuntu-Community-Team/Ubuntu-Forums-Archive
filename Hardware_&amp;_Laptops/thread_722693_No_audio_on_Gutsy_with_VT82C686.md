---
title: "No audio on Gutsy with VT82C686"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by Aflibo on 2008-03-12
I've installed Ubuntu 7.10 but I get no sound. My sound card is a VT82C686 (AC97) integrated on a GA-7ZX motherboard. If I do lspci the sound card seems to be detected and if I do lsmod | grep snd I see that snd_pcm and snd-ac97-codec are loaded but when I do cat /proc/asound/cards I get "no sound card".  Any hints?

---

