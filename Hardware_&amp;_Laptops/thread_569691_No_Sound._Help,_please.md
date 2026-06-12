---
title: "No Sound. Help, please?"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by MariusEriksen on 2007-10-07
Hi, I'm running Ubuntu 7.06.
The problem is that I don't got any sound at all.
SPECS: Pacard Bell with a Realtek ALC861-VD sound card. (intergrated, I think)

Can anyone help me get my sound to work? Really anoing stuff..
One more thing, everything work perfectly on Ubuntu 6.06, so is it posibly to reload to the 6.06 sound devices? 
*********************
Pleas help. Thank you!

---

### Post by linuxican on 2007-10-09
Hi,
I've got the same card on my lenovo N200, so far no success. google this forum for it you'll find colorful solution, hope they work for you.
Good Luck

---

### Post by alex.a.mandl on 2007-11-02
My laptop Lenovo 3000 N200 is TY2B8HV. I inserted "options snd-hda-intel index=0 model=lenovo" line in the file /etc/modprobe.d/alsa-base. I restarted my system and now, the sound is perfect. Enjoy :popcorn: !
sudo echo "options snd-hda-intel index=0 model=lenovo" >> /etc/modprobe.d/alsa-base

---

