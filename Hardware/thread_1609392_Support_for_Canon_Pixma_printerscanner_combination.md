---
title: "Support for Canon Pixma printer/scanner combinations, especially newer models?"
date: 2010-10-30
forum: Hardware
---

### Post by Rumtscho on 2010-10-30
I want to buy a printer/scanner combination. For now, my choice is the new Pixma MG8150, because I've read very good reviews of Canon print quality. But as this model is very new, I don't know if it will work with Ubuntu. Actually, I've never tried to make a Canon printer work with Ubuntu, and I don't know how the driver situation is. 

If someone has used a Pixma combi-device under Ubuntu, please tell me if you'd recommend it. Are the drivers easy to install, do they support all functions, and how long does it take to get the newest models supported? It would be perfect if you had experience with the exact model MG8150, but if not, then info about the older models would be interesting, too. 

And a side question: is there a way to make a forum search within the "compatibility list" thread? It is nice that it exists, but it has 70 pages now, and paging through it searching for a specific hardware model is too tedious.

---

### Post by woodmaster on 2010-10-30
Stay away from Canon!

---

### Post by stuartmetcalfe on 2010-12-03
Canon provide drivers for this device but they only seem to be available from their Asian support site for some reason.  They're available as .deb packages and seem to work with Maverick.

The printer drivers work for me over the network:
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100301902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301902.html)

The scanner driver installed fine but I haven't got it working yet:
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100303202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100303202.html)

---

### Post by stuartmetcalfe on 2010-12-03
Canon provide drivers for this device but they only seem to be available from their Asian support site for some reason.  They're available as .deb packages and seem to work with Maverick.

The printer drivers work for me over the network:
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100301902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301902.html)

The scanner driver installed fine but I haven't got it working yet:
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100303202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100303202.html)

---

### Post by stuartmetcalfe on 2010-12-03
> **stuartmetcalfe said:**
> The scanner driver installed fine but I haven't got it working yet

Turns out that Canon's scanner driver package installs the scangearmp app.  Run that and it'll work with both network *and* USB :)

---

### Post by yahozna on 2011-01-13
> **stuartmetcalfe said:**
> Turns out that Canon's scanner driver package installs the scangearmp app.  Run that and it'll work with both network *and* USB :)

It indeed does work (received my new Canon Pixma MG8150 yesterday).

One problem: the scanner comes with the possibility to scan negatives, however the scangearmp app does not give you the possibility to select 'negative' as source............bummer :(

The ability to scan negatives was exactly the reason to buy this device.....

---

### Post by john stiles on 2012-01-17
Received my MG8150 yesterday. All installed fine, drivers now available on Canon UK site. Great for the family to be able to print to centrally whatever their OS.

Thanks for advise and prods in this post.

---

### Post by aikishugyo on 2012-01-20
The two open source projects that support inkjets and scanners, respectively, on linux are gutenprint (also on MacOSX) and SANE.

As the maintainer of the Canon backend in gutenprint, I can say that support for the newest Canon's is certainly there, and similarly support is in SANE too (there is a new and energetic junior developer, who is prepared to accept and submit patches and correct problems).

One disadvantage of the gutenprint driver currently is that the multi-pass code has not yet been ported from the Epson backend, so the maximum resolution is limited to 600dpi, which is not good enough for photos really.

Also, tuning (profiling) may need to be done for the colors, depending on the printer.

Apart from that, printing to all media, many more sizes than the native Canon driver offers, and CD printing all function. Bugs that are reported are solved as quickly as possible.

So while Canon do have their own software available for some models, please keep in mind that the open source community is very active in trying to get 100% support for all models as well.

---

