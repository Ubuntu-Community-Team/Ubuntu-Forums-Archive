---
title: "Sound Does not Come through the Speaker"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by csshyamsundar on 2007-04-22
I have an ACER 5052NWXMi Laptop., running Vista and Feisty Fawn!

System Config:
AMD Turion X2 ( 1.6 GHz ).
ATi RADEON XPRESS 1100 with 256 MB shared memory.
120 GiG HDD and 1.5 GiG DDR RAM ( I upgraded 1 GiG RAM with its default 512 MB RAM ).
Broadcom Bluetooth and Atheros 5005 802.11 b/g WiFi Card.
Realtek High Definition Audio as Sound Card.

---

The ONLY issue is with Sound, that too it plays perfectly when I plug the headphone, but it does not come out through Speakers.

Everything else works out of the box, incl. Atherox WiFi and ATi graphics :) 

Can anyone help me setright the Sound Issue :confused:

---

### Post by heimo on 2007-04-22
First thing I'd do is to open terminal, type "alsamixer" and check that there are no muted channels (m key to toggle), sliders are not all the way down. Use arrow keys and tabulator to navigate (there may be more channels to the right, "hidden" at first).

---

### Post by csshyamsundar on 2007-04-22
Thanks!

[ I switched the "headphone" option of "Surround" !!! and now works !!! thank you 'heimo'., may the forces be with you :guitar: ]

---

