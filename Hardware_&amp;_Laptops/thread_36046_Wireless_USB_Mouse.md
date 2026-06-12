---
title: "Wireless USB Mouse"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by kinetix63 on 2005-05-21
Hi Guys,

I've tried searching the forums, but unfortunately haven't yet found an answer - I hope someone here can help!

I've just installed 5.04 - works like a dream, however my MS wireless mouse seems to be causing a problem. It seems to both a) register random mouse clicks, and b) when I actually press the mouse buttons, it seems very random as to whether or not the thing responds.

I don't know if this is something to do with the fact that the combo uses only one wireless base station, and for some reason linux isn't interpreting the signal properly - but the problem is driving me beserk! Any help would be greatly appreciated.

Thanks,

Paul.

---

### Post by jonrkc on 2005-05-23
I use a Logitech wireless optical mouse, and it works perfectly under 5.04.  

You might check the /etc/xorg.conf file and see what type of mouse the system thinks it is dealing with.  I believe, though I'm not certain, that all Microsoft mice should be considered "Intellimouse" type.  At any rate, it won't hurt to try different configurations.  (I'm sure you'll keep a copy of the existing xorg.conf file under a different name in case something goes really wrong and you have to replace the one you've edited!)

Good luck!

---

