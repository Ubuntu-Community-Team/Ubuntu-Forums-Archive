---
title: "Toshiba Sound driver"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by xorocs on 2007-06-11
So, I just installed Ubuntu on my Toshiba Sattelite P105-S6024 laptop, and the sound wont work, I tried to find drivers for it, but wasnt able to .. so what do you guys think i should do.

---

### Post by VMan on 2007-06-12
I had the same problem with my Toshiba A135-S4467.  I think we have the same sound cards (not sure though).  Search these forums using "sound" and "A135".  There is a fix listed by adding one line to your /ect/modprobe.d/alsa-base file.  I worked great for me.  Let me know if you can't find it, and I'll look it up for you.  Hopefully the same fix will work for you as for me.  Apparently, Ubuntu finds the modem first and tries to use it as the sound card.

---

### Post by stchman on 2007-06-12
> **xorocs said:**
> So, I just installed Ubuntu on my Toshiba Sattelite P105-S6024 laptop, and the sound wont work, I tried to find drivers for it, but wasnt able to .. so what do you guys think i should do.

I have a Toshiba A135-S2246 with the SB450 sound card.  This worked for me:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

If not then you will need to update the ALSA driver.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

The first one should work if you have the SB450 sound card.

---

