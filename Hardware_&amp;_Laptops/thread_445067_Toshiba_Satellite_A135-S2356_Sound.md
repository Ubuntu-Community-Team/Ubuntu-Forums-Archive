---
title: "Toshiba Satellite A135-S2356 Sound"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by orangecakez on 2007-05-15
I have a Toshiba Satellite A135-S2356, and I can't get sound even when I added the line "options snd-hda-intel model=3stack" to the bottom of /etc/modprobe.d/alsa-base. I saved and rebooted, but still to no avail. It says there is no hardware detected, and I don't even have a sound volume controller thing (to raise or lower the volume; I can't get that because there is no sound hardware detected). How can I get sound on this model? Drivers don't work. I got ALSA.

---

### Post by mostholy on 2007-05-19
I have a Toshiba Satellite A135-4527 and was finally able to get the sound functional after following the alsa recompile instructions here: 
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)
Note that the sound gets muted and you will have to undo that in alsamixer and reboot.  

Hope this helps.

---

