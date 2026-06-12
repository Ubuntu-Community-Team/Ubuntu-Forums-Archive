---
title: "ENE Card Reader again"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by Sianis on 2005-10-16
Hi!

I have a Ene card reader in my laptop. I read many for this product, but i didin't find driver for this, and i read there isn't yet. So the Ubuntu theme can write this or not? Or can i fix this probleme?

My  lspci write this:

```
0000:01:09.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 01)
0000:01:09.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller

```

Please help me, or do we somthing, cause i wanna use this, and not under windows...thanks!

Sianis

---

### Post by ola18 on 2005-10-16
I got the same problem, my lspci can detect it but i dont know how to access.

Is it just for us to mount? what category in /dev do i mount in that case..

---

### Post by Sianis on 2005-10-17
I thing it works like an USB Pendrive, but need river first, and that's not reachable...now, so i thing this hardver cannot acces in /dev/...

---

### Post by Sianis on 2005-11-06
PLS help in this question!

HAL see the device, lspci see the device, but don't work, why? Can anybody help me? :confused:

---

### Post by dninja on 2005-12-16
Did you get anywhere with this? Has anyone managed to get one of these working?

---

### Post by Circleback on 2006-04-27
Hey I live right down the road from these guys. Maybe ill go by and throw a rock through their window with a message on it from all the frustrated Acer and Asus/Linux laptop users.

---

### Post by dangermouse28 on 2006-04-28
The ENE card reader is also used in Compaq ZD7000 laptops. On the ZD7000 forum, someone installed Mandriva 2006 Power Pack and found the card reader to be fully functional as opensc was installed by default. ([http://www.zd7000forums.com/viewtopic.php?t=5605&highlight=opensc](http://www.zd7000forums.com/viewtopic.php?t=5605&highlight=opensc)) I haven't looked into it but this could be the way forward.

---

### Post by Sianis on 2006-05-17
Not good. It isn't Smart Card Reader. SD/MMC card reader. In ZD7000 the SC reader is an other device i think. 

The ENE didn't reply for me yet and they will never send me positive mail... :( 

This device will never work on Linux.

---

### Post by gobbolino on 2006-07-06
i have the same problem with my laptop... some solution? :confused:

---

### Post by dptxp on 2007-03-17
ACER seems to be paid by Microsoft. So is ENE. They mark their laptops VISTA-Ready. And can not even give drivers for Linux.

---

### Post by HarshReality on 2007-06-25
> **dangermouse28 said:**
> The ENE card reader is also used in Compaq ZD7000 laptops. On the ZD7000 forum, someone installed Mandriva 2006 Power Pack and found the card reader to be fully functional as opensc was installed by default. ([http://www.zd7000forums.com/viewtopic.php?t=5605&highlight=opensc](http://www.zd7000forums.com/viewtopic.php?t=5605&highlight=opensc)) I haven't looked into it but this could be the way forward.

Just because I am aware... I too found the post listed and also have a zd7000 (modified) so on a whim I tried his approach. He was so hardup on bragging about Mandriva that he didnt even check the onboard card reader (he was using a USB version). So after staying up till 4am this morning I can say for a fact that 2K6 & 2K7 do NOT have the out of box approach going on for them. To be honest I didnt see anything Mandriva had to offer that Ubuntu doesnt outside of they made icons for pictures, media & videos and even had the windows key mapped so it could be more "windows like".

---

