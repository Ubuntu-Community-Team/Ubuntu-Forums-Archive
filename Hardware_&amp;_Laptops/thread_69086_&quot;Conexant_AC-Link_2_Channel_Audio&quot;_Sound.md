---
title: "&quot;Conexant AC-Link 2 Channel Audio&quot; Sound card can't work!"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by caocheng on 2005-09-25
Conexant AC-Link 2 Channel Audio  card has been recoganized as Intel I810 AC97. My notebook can not sound out. But the applications is still working and no error worning.

Where can I found the driver the this Audio card? Alsa dosen't support it.

Are there any other solutions to this problem?

---

### Post by mlomker on 2005-09-25
Try **dmesg | grep snd** at a prompt to see what drivers are loading.

---

### Post by caocheng on 2005-09-26
dmesg:
 
    snd_i810

lsmod :  snd_i810 ....

---

