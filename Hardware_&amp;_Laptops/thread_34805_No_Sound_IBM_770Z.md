---
title: "No Sound IBM 770Z"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by saladbarkid on 2005-05-16
I'm trying to get the sound working on my IBM 770Z laptop.  I can get it to work by going into a root terminal and typing modprobe cs4232.  I tried to automate the process by adding snd-cs4232 to /etc/modules and that makes the sound skip like crazy!

Is there a way to get this sound working?

---

### Post by gna on 2005-05-27
I don't have ubuntu BUT i got (the speakers) working:

Alsa Module: snd-cs4236 (its a ISAPNP module but with Debian Sarge it works)

My problem, i cannot record from the microphone, so i can't use for example Skype.

Anyone?

---

