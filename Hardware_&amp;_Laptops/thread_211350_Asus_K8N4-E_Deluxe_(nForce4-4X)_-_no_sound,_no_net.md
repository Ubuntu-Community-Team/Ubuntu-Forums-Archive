---
title: "Asus K8N4-E Deluxe (nForce4-4X) - no sound, no net"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by zaubara on 2006-07-08
Hey!

I just wanted to ask you guys, if there is a short workaround to get networking and sound working on my mainboard?
I think these don't work because I'm using a nForce4-4X mainboard, which includes S754 and PCI-E on an nForce4 ](*,) 

Thanks,
Martin

---

### Post by lawngn0mex on 2006-07-09
have you tried downloading the alsa files, building them, then running alsaconf?

[http://alsa-project.org](http://alsa-project.org)

---

### Post by zaubara on 2006-07-09
Nope, I didn't - but I found a (way too simple :-s) solution - adding acpi=off to my bootline fixed all my problems.
Maybe I didn't think of this at first, because restarting and shutting the system off worked fine :/

Thanks for your help and patience though :D

---

