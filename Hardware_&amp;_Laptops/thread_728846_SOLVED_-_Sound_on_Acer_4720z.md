---
title: "SOLVED - Sound on Acer 4720z"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by WhiteHorse on 2008-03-19
Here's how I got sound working on the Acer 4720z laptop. I did this after getting all updates:

sudo gedit  /etc/modprobe.d/alsa-base

Enter the line

options snd-hda-intel model=acer

---

