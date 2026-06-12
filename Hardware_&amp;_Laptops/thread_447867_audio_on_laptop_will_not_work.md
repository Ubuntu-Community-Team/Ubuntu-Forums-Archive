---
title: "audio on laptop will not work"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by jrippke on 2007-05-18
The audio on my Gateway 4520GZ with an intel 82801DB/DBL/DBM sound card will absolutely not work.  I was able to see the device in my hardware devices listing and I did the system audio checks.  The volume is all the way up.  I'm new to Ubuntu/Linux and I really like it so far, if I could just get the sound to work.  I can't find any drivers for the card for linux and I've looked everywhere in the forums and tried quite a few tips I found, but to no avail.  someone please help.

thank you
-Joe

---

### Post by Kobalt on 2007-05-18
Check [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") out first.

---

### Post by stchman on 2007-05-18
> **jrippke said:**
> The audio on my Gateway 4520GZ with an intel 82801DB/DBL/DBM sound card will absolutely not work.  I was able to see the device in my hardware devices listing and I did the system audio checks.  The volume is all the way up.  I'm new to Ubuntu/Linux and I really like it so far, if I could just get the sound to work.  I can't find any drivers for the card for linux and I've looked everywhere in the forums and tried quite a few tips I found, but to no avail.  someone please help.

thank you
-Joe

What kind of sound card does lspci say you have?  Please post the lspci listing here.  Are you running Feisty?  Intel chipsets are usually supported out of the box.

---

### Post by jrippke on 2007-05-23
this is what my says when I lspci:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

I've tried everything I can find, still nothing works, please help.

---

