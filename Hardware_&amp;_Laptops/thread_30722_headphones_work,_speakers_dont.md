---
title: "headphones work, speakers dont"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by vb7prog on 2005-04-29
ok, my problem is going to sound like a broken record but i can assure you not only have i checked the forums extensively I've wasted alot of personal time as well.

I have an Audigy 2 platinum  and it comes with a special 5 1/4 bay expansion port, thru the expansion port, i get cyrstal clear sound( its 2.0 sound made for headphones);however, straight out of the back my 5.1 speakers get no sound ever, i plugged my headphones in the back and they get nothing as well.

I tried messing with reinstalling alsa and all this stuff but it has reached a point where i can't use ubuntu if i can't have sound.

was using Ubuntu 5.04

---

### Post by Seth on 2005-04-29
[QUOTE=vb7prog]ok, my problem is going to sound like a broken record but i can assure you not only have i checked the forums extensively I've wasted alot of personal time as well.

I have an Audigy 2 platinum  and it comes with a special 5 1/4 bay expansion port, thru the expansion port, i get cyrstal clear sound( its 2.0 sound made for headphones);however, straight out of the back my 5.1 speakers get no sound ever, i plugged my headphones in the back and they get nothing as well.

I tried messing with reinstalling alsa and all this stuff but it has reached a point where i can't use ubuntu if i can't have sound.

was using Ubuntu 5.04[/QUOTE]
 $ alsamixer

Unmute the Analog / Digital Out (to switch it).

$ sudo alsactl store

Grood.

---

### Post by vb7prog on 2005-04-29
holy crap, thanks so much

---

