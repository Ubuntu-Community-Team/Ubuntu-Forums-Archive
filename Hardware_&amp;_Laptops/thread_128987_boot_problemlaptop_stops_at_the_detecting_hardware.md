---
title: "boot problem:laptop stops at the detecting hardware to find cd drives"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by harys on 2006-02-12
hi, i booted my laptop ACER TRAVELMATE 516TE from cd drive with cd live ubuntu but at the detecting hardware to find cd rom drives (message into bar : loading module 'ide-cd for linux ATAPI cd rom...). the computer stops checking at 86% and i had to power off. i tried a second time but had the same result. pls help. what should i do at this point. thanks. arys

---

### Post by djpsd on 2006-02-19
Same exact problem here !

Stops at 86% if I use the install cd or live cd. I have almost the same computer, mine is a Acer Travelmate 514txw

---

### Post by saschaz on 2006-02-23
I have an Acer Travelmate 529 TXV. Same problem with installation.

But I found a work-around!!! Boot from CD. Then (at the prompt) type:

boot> expert noapic nolapic pci=noacpi

You will then see kind of a menu with several installation steps. After chossing your language continue installation with CD ROM detection.

The detection of the CD ROM drive now completes successfully (it's magic). Don't know exactly why or if this works on other (acer) notebooks.

Hope this helps :-)

---

### Post by teh_louis on 2007-06-04
It seems that the following above are quite noobed, I, you see, have managed to run Ubuntu (live) on a PPC Mac (OS X 10.4.9) which is quite a feat you see. If you find this "86%" problem try doing a divert boot using the failure file.

Teh_Louis

---

