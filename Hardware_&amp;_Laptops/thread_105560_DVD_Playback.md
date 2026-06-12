---
title: "DVD Playback"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by mrgnash on 2005-12-18
I'm experiencing extremely poor playback for DVDs... I installed all the decoders and so on as per the instructions on the Ubuntu Wiki... even so, the only player that 'worked' was Gxine. I installed the ATI Linux drivers as I'm using a Mobility Radeon X700 (my laptop is an Acer Travelmate 4402WLMi) but this didn't seem to improve performance at all, apart from messing up my resolution until I went in and configured it manually.

---

### Post by snowjunkie on 2005-12-18
Have you enabled DMA?

---

### Post by mrgnash on 2005-12-18
I dunno, where would I go to enable that?

---

### Post by Ptero-4 on 2005-12-18
You use hdparm. But be careful it's a quite powerful util and with the wrong command can do quite nasty things on your drives.

---

### Post by mrgnash on 2005-12-18
Thanks, I followed the link Daller sent me and it worked :)

---

### Post by snowjunkie on 2005-12-19
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447)

---

