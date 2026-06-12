---
title: "Suppress empty page after completing print job"
date: 2008-09-27
forum: Hardware
---

### Post by schmandr on 2008-09-27
Hello!
After completing each print job, my printer ejects an additional empty page, wasting quite a bunch of paper. It may be due to my setup:
My printer is a HP LaserJet 1022, connected via USB to a Siemens Gigaset SE 551 WLAN dsl/cable wireless router. I'm using CUPS 1.3.7, Printer Driver: HP LaserJet 1022 Foomatic/foo2zjs, Device URI: lpd://192.168.2.1/LPT1

Any ideas how I can suppress the empty page? Thanks!
Andreas

---

### Post by schmandr on 2008-10-04
Problem still persists. However, there is no empty page produced if the printer is connected directly to the computer via USB. So it seems the problem is the LPD queue on the wireless router.
Is there a different way for this than using an LPD queue? Or any parameter to set?
Any help is still highly appreciated.

Cheers

---

### Post by Bazon on 2011-12-06
I have the same problem (apart from using a desktop pc with xubuntu) with a ldp printer:

I have a new router (Speedport W 921V) which has USB ports on which I connected my printer (HP DeskJet 950C).

Printing works (URI: lpd://192.168.2.1/lpt1), but after each job, the printer sucks out one extra blank page.

How can avoid this extra non printed page?

Is there now a solution or workaround?

---

