---
title: "soundblaster vs onboard sound card"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by kochab on 2005-05-31
hi,
I have a sound blaster 5.1 and a SiS motherboard sound device, how can I set the soundblaster as default sound device?
I've even tried to disable the onboard device from BIOS but I didn't manage.
many thanks!

---

### Post by jkndrkn on 2005-05-31
Are you using alsa? If not, I recommend setting it up. Try this howto:

[http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+howto](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+howto)

Be sure that the line pcm "hw:0,0" points to the soundcard of your choice. That's all I needed to get my soundblaster live to be set to default.

---

### Post by kochab on 2005-06-02
Yes, I'm using alsa, and changing the pcm line solved the problem, thank you!  \\:D/

---

