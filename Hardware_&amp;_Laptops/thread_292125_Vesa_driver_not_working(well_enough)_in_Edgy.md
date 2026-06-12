---
title: "Vesa driver not working(well enough) in Edgy"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by lastcyrol on 2006-11-03
Hello Ubuntu community. The problem I have is really annoying, and I really hope, that there is someone who can help me solve it.
I recently(today as a matter of fact) upgraded my Dapper to Edgy. I did it mostly, because I found out, that the xserver-xorg-video-trident 1:1.2.1-0ubuntu1 finally includes a patch for making my XGI Volari XP5 video controller work in a way different than vesa compatible mode. Only the thing is, it stopped doing even that. When I restarted the notebook(ECS 532 with Transmeta Efficion CPU) there was no picture on screen. There is the situation. The vesa driver won't work. No graphics, no virtual console. Only the single mode works always. The trident driver goes the same way. The fb(or fbdev) driver makes it, the console works and it shows graphics, but incorrect, the the picture takes only 70% of display height and places 5 times in width with overlapping. The colors are wrong too. 
Any other driver would let the console work, but X won't start.
Is there anybody who knows whats wrong, at least with the vesa driver?

---

