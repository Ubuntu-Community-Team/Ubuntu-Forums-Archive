---
title: "Laptop as second monitor???"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by not_cool on 2006-11-25
I was wondering if it would be possible to attach my laptop to my computer and have it run as a second monitor. it would use my vga connection, the main monitor would have dvi (but could be vga also if needed). My video card is a nVidia Geforce FX 5200 with one dvi and one vga connection. When I tried simply hooking the laptop up without configuring xorg.conf or anything and booting both computers, the main monitor lost it's connection and the laptop had a black screen. I'm using the 1.0-9742 version of the nVidia beta drivers, which are the latest ones.

---

### Post by audax321 on 2006-11-25
I saw this done somewhere before (I was looking for the same solution) but it involved ripping the laptop apart and reconfiguring the cables coming from the LCD to its internal video card. It was pretty ugly and not very practical :)

The problem with what you want to do is that laptops have VGA ports that allow video out from their video card, not video input. Now if you wanted to use your desktop monitor as a second monitor you could with your laptop. But not the other way around.

The easiest solution to what you want to do is to get another monitor if your existing video card has an additional video output (two-head video card - I only have experience doing this with nVidia cards). Also just because your video card has two video outputs does NOT mean it is dual head. You'll need to check the specs for the particular brand of video card you have. Otherwise you'll probably need to get an extra video card and another monitor (I have NO experience doing this).

---

### Post by not_cool on 2006-11-25
Thanks for the info. My card is dual-head so I guess I'll just get my old crt monitor out and hook that up...

---

