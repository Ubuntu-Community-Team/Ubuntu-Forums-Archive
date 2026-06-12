---
title: "Acer Travelmate 225XV TFT"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by topic58 on 2005-09-24
I got a problem installing Ubuntu 5. When using installCD my TFT-screen becomes full of lines. I cant se anything at all. The welcomescreen when I open Ubuntu installCD is okay, but after that it has a lot of lines all over it. When using liveCD is was the same, but when liveCD was loaded the screen was okay again. My CD has 8xDVD and CD, no burner. What to do here? Any suggestions at all? Have tried both 5.04 and 5.10, the same with both. Dont know much about my graphic card. Can someone please help me out here?

---

### Post by fordfan753 on 2005-09-24
It's probably setting your resolution too high. Press Control + Alt + F1 and login. Type "sudo dpkg-reconfigure xserver-xorg" go through all the options, and when it gets to screen resolution there should be three options, simple, medium, advanced (or something like that) choose medium, and select 1024x768 @ 60 Hz, most screens are capable of this and should display it perfectly.

---

