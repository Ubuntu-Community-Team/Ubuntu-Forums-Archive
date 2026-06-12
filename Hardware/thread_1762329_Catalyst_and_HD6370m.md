---
title: "Catalyst and HD6370m"
date: 2011-05-19
forum: Hardware
---

### Post by xape on 2011-05-19
hi,

I installed Ubuntu 10.10 on my hp 4520s (  with Radeon 6370m ). 
The default installation sets ati proprietary drivers and Catalyst 10.12 version, as I read in the Catalyst windows. With these drivers I see, at the bottom right of the desk, "Unsupported Hardware Watermark " and if I write on a terminal "aticonfig --initial -f" I see "No supported adapters detected".

So, I installed new drivers's version (11.5) from AMD site, during installation I had no errors and fglrx drivers work fine (what I see in Catalyst  information windows) but catalyst version is still 10.12. 
I try to delete all amdcccle file on the system and install another time the drivers but I obtained same results, ati Catalyst version 10.12 with the "Unsupported Hardware Watermark ". 
 

Somebody found this problem?
Suggests

Best regards

Andrea

---

### Post by hacksolidus on 2011-05-19
Hi Andrea, I have a solution for this, its a little Script to remove the Watermark.
You need execute this Script in Terminal with Super User permissons.
If you have the Script in Downloads directory you need to make:

cd /home/user/Downloads
sudo sh watermark.sh

After this reboot the system and enjoy.

---

### Post by xape on 2011-05-19
Thank's , this evening try it... and let you know.

Andrea

---

### Post by xape on 2011-05-19
just a thing, do you know what'is the problem with aticonfig? 
If I write aticonfig --initial -f I obtain "No supported adapters detected"

thanks

Andrea

---

