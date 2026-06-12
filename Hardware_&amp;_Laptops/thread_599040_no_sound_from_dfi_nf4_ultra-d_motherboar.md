---
title: "no sound from dfi nf4 ultra-d motherboar"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by nanjil on 2007-10-31
i know the motherboard audio is realtek , not nvidia. I selected therealtek ac-850from sound preferences . still i am getting no sound
any clues, work around?

thanx

---

### Post by proteo on 2007-10-31
You can try to move the jumper next to the karajan module, check your manual, to use the nvidia codec instead of the realtek, that's the way i'm using it, and it's working fine. hope that helps.

---

### Post by nanjil on 2007-11-01
I should try that. But in the mean time I installed an audigy 2ZS sound card , that also does not work. Is my sound settings corrupted?

---

### Post by proteo on 2007-11-02
what version of ubuntu are you running?
I had a lot of troubles with sound on Feisty, but i think it was my fault because I was trying to use the OSS driver for my X-Meridian and the ALSA for the onboard audio, but most of the problems solved when I upgraded to Gutsy, even if I lost the support for the X-Meridian (the driver is too buggy and it's disabled by default).

---

