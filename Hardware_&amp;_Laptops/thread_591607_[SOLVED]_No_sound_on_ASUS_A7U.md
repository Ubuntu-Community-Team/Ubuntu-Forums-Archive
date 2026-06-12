---
title: "[SOLVED] No sound on ASUS A7U"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by henklaak on 2007-10-25
Hello,

My new Asus A7U is quiet, a bit too quiet even, since I can get no sound on my speakers or headphones. I have another similar Asus laptop (5FR), that works perfectly. It has the same audio hardware as far as I can tell. Both have fresh Ubuntu 7.10 installs.

I have checked all the obvious things, done my research, followed  [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")  and I am stuck, bad.

Driver seems to work (no error messages), I even have the microphone working (Audacity shows the VU meters moving properly).

Details in: [http://www.pastebin.ca/749731]("http://www.pastebin.ca/749731")

Any hints?

Thx, Henk.

---

### Post by henklaak on 2007-10-26
Anybody?

---

### Post by henklaak on 2007-10-28
Solved it! Yesssssssssss!!

This excellent howto: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
made it possible.

I built the latest ALSA drivers 1.0.15 and needed to add this line to my /etc/modprobe.d/alsa-conf file:

options snd-hda-intel model=auto

I don't know if the 1.0.15 was necessary, but I'm not going back to try it out. A working system doesn't need fixing, right?

Gr. Henk.

---

