---
title: "Nvidia GT540"
date: 2012-12-06
forum: Hardware
---

### Post by sauzer00 on 2012-12-06
It's just a question.
I have an acer aspire 5755G and when i ceck 
"computer information" under "graphs" i get a common video card 
instead my Nvidia GT 540.

I also get an lspci and this is the output

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

and also
sauzer00@sauzer00-Aspire-5755G:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)

So this card should work but look like that the system is using the other integrated card.
Everything is working fine on both my monitor, the resolution it'ok but, since i have that better card i would like to use it 
There is a way to get the propertly drivers ?

---

### Post by Yellow Pasque on 2012-12-07
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by sauzer00 on 2012-12-07
Ok working 
now if i do a lspci

this is the answert
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)


Thanks guys :)

---

