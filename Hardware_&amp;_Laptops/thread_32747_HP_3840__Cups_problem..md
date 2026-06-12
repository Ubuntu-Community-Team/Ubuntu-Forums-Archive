---
title: "HP 3840 / Cups problem."
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by gorby on 2005-05-09
Hi there im having some problems with printing from my grannys Ubuntu box.
Here is the scenario:
I installed warty on my grans laptop (a Hp nc something) @ Christmas.
	My Gran has v minimalist requirements from box. All she has used over the last 6 months is open office, evolution and gaim. It has worked faultlessly since Dec (the printer installed fine via gnome-cups ui using the 3840 ppd file), but around a week ago the printer stopped printing. 
It still looks as if its printing (the carts move over the paper but nothing is printed ONTO the paper.)

Here are my thoughts / what I have tried.
	Not a cart issue, printer still prints fine from a winblows box.
	It had been a long time since any kind of upgrade, so I apt-get updated and then did apt-get distupgrade. This amongst other things brought the kernel upto 2.6.8.1.5 so I had to update a few modules, nothing major. Still same issue afterwards.

	There is nothing (I can see anyway!) unusual in /var/log/cups. Just the same block that had been repeating since it was installed.

Like I say guys im pretty flummoxed, and this is pretty difficult because im doing it all via VNC / SSH with my gran watching the printer with phone in hand!

Any help appreciated.

---

