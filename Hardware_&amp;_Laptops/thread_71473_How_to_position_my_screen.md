---
title: "How to position my screen"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by ac82 on 2005-10-03
Hi!!

I installed Ubuntu, and discovered following problem:
In resolution 1280*1024, my desktop is positioned about 20% to right, off the screen. I've modified xorg.conf (monitor part) to settings provided by manufacturer of my monitor(Hyundai ImageQuest L50s), I've tried using auto-adjust, installing nvidia drivers(Asus v9999gt(6800gt 128mb)). Display works normally in Windows or when using 1024*768 in Ubuntu. Where's the problem, I dunno. Please help someone.

---

### Post by Seth on 2005-10-03
Run xvidtune, and position your screen how you want it. Generate a modeline (it will dump it to console) and exit. Paste your new modeline into xorg.conf in the right spot. It'll work :)

---

### Post by ac82 on 2005-10-03
That worked, thanks!!!

---

