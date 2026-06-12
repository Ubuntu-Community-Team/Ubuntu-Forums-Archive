---
title: "No sound Lenovo 3000 N200"
date: 2008-06-29
forum: Hardware
---

### Post by asjad on 2008-06-29
Hi all,

I installed Ubuntu 8.04 on my Lenovo 3000 N200 laptop. everything seems to work fine except the sound. i dont hear any sound immediately after booting and while playing music from any players i have Amaraok, Xine etc. With little research on this topic i found that editing alsa-base file from root i.e etc/modprobe.d/alsa-base and adding  model ="Lenovo" would correct the sound problem. but when i typed sudo, it doesnt ask me for password nor i am able to edit it with a command sudo gedit etc/modprobe.d/alsa-base. 

Please help me :guitar:

Thanks in advance 
Cheers

---

### Post by marconicotera on 2008-06-29
Hi, 
here's a very usefull link. U have to check your sound card model and follow the instructions. 

[http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+sound+issues](http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+sound+issues)

---

### Post by asjad on 2008-06-29
Thank you very much for the valuable information. sound works !!!!

hurray!!!!!!!!!!:guitar:

---

