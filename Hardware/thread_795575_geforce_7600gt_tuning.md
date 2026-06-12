---
title: "geforce 7600gt tuning"
date: 2008-05-15
forum: Hardware
---

### Post by csulok on 2008-05-15
Hello there

I have an Inno3D Geforce 7600GT videocard that I'd like to - to reduce heat generation - downclock. I found a great tool for this called "nvclock".

With it, I changed the gpu speed from 560Mhz to 200Mhz (using sudo nvclock -n 200). This reduced the temperature from 65 degrees to 58. 

When I tried to modify the memory speeds (from 1400Mhz (700 ddr) to 1000Mhz), the picture on the display just broken up, so I guess memory speed alteration is not possible... or do I set it from 700 to 500? 

My second question would be if it's possible to change the voltage of my videocard from 1.30V to something lower, afaik with this severly reduced gpu speed a much lower voltage would be sufficient too. Does this card support voltage customization? I don't want to test it before someone says something definite about it.

My third problem is that the changes made don't get saved. After rebooting I still find the card running at default speeds. How do I change this? I noticed there are 2 performance levels with identical speed and voltage settings, the first probably for 2d, the other for 3d. How do I change the 2d performance options to these lower speeds?

Thank you

---

