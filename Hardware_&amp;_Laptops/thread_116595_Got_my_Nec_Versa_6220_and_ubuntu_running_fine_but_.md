---
title: "Got my Nec Versa 6220 and ubuntu running fine but NIC is a no-go...please help."
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by shaolin95 on 2006-01-13
Hi!
As expected based on my research here, the NIC is not working for my laptop. I tried using the acpi=off as I read here but it didnt work (or I didnt do it right). Anyone can help me get the internet going please?
BTW, at 200MHZ and 128MB ubuntu is slow to load but practicing Python is no trouble at all.
Regards

---

### Post by shaolin95 on 2006-01-13
Just to add the ethernet card is a xircom xe2000.
I tried this at terminal ""sudo modprobe xirc2ps_cs"
but it did nothing.
I tried this:sudo cardctl ident
and it shows my card correctly identified.

I just did cardinfo and it shows the Xircom XE2000 in an neat info window. Still cant connect though...

UPDATE:
ITS WORKING! How I am not sure. The last thing I did was enter acpi=off on terminal and then tryied ping yahoo.com and got possitive results so decided to try mozilla and boom it worked. I wish I knew how but for now I am happy!


PLEASE CLOSE THIS THREAD...ITS BEEN SOLVED! Thanks :-)

---

