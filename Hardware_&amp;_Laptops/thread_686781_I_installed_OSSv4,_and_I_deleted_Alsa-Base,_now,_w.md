---
title: "I installed OSSv4, and I deleted Alsa-Base, now, when I plugg in the headphones....."
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by the_analyzer on 2008-02-03
like the title said I have problem listening with headphones in my acer laptop. so I installed OSSv4, and I deleted alsa-mixer, now when I plug in the headphones and play music, the music is played from the laptop speaker also (not only from the headphones)

It exist and another proble, I dont have anymore the volume icon in the upper-right screen and I cannot control my volume anymore.
Please, I would appreciate very much if you hellp me.

---

### Post by Wim Feijen on 2008-02-03
Try running:
gnome-volume-control

and maybe choose File > Change Device. I wonder whether this helps.

---

### Post by Yellow Pasque on 2008-02-03
Use ossxmix to control the volume. There's also a patch by Clive Wright that makes gnome-volume-control work with your mouse wheel and such. Follow the link in my signature.

---

