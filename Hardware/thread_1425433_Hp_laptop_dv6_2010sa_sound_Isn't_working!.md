---
title: "Hp laptop dv6 2010sa sound Isn't working!"
date: 2010-03-09
forum: Hardware
---

### Post by mcds2 on 2010-03-09
Hi, the sound on my laptop refuses to work for some reason, it knows there is a sound card but it won't play any music or let any sound escape! please help!

---

### Post by Fafler on 2010-03-09
Has it worked before? What sound card does it have? Use lspci to find out. I have seen some flakyness with the Intel HD audio card present in many C2D based laptops. sudo rmmod snd-hda-intel && sudo modprobe snd-hda-intel (from memory, module name might be different) to fix.

---

### Post by mcds2 on 2010-03-09
No, the sound has never worked with ubuntu i'll have to check the sound card that is used i'll post that later!

---

### Post by mcds2 on 2010-03-09
The Devices are ATI High Definition Audio Device and there is a IDT High Definition Audio Codec.

---

### Post by mcds2 on 2010-03-09
bump

---

