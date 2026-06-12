---
title: "problems booting ubuntu 6.1"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by ikem on 2007-05-17
i have a dell dimension 2300 and i can load grub and the splash appears. also, starts loading and stops about 20% the way though. any advice.

2.0 ghz pentium 4

256 mb ati radeon

---

### Post by iheartme on 2007-05-17
Try editing your grub boot line (pressing escape at the first prompt, then "e" to edit the line) and remove "quiet" and "splash". That way you'll temporarlily remove the splash screen and you'll be able to see where it stops exactly.

The line to edit is the one with root=UUID=xyxy (or something like that). Sorry that I can't be more specific, my memory fails me at the moment, but you'll know when you see it if you don't already know what the heck I'm talking about :)

---

