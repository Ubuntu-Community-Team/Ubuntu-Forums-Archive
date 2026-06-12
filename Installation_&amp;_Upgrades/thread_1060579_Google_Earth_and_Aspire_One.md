---
title: "Google Earth and Aspire One"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by BazookaAce on 2009-02-04
Hi, 

I downloaded and installed Google Earth 5.0 on my Aspire One A150, and when i start it, it says that my resolution is to low. Google Earth requires 1024x768, and my screen displays 1024x600 pixels. Is there a way to maybe config it or am i lost? The funny thing is that i'm only 178 pixels from making it!

Help?

---

### Post by pauwl on 2009-02-05
There is a xorg setting something like:

```

Section "Screen"

Subsection "Display"
		Virtual	1600	1200

```

I **think** if you edit this and set it to your required size, you should be able to "pan" and install google earth.

Here another thread that has to do with virtual sizes - but there's probably a lot more out there:

[http://ubuntuforums.org/showthread.php?t=816825](http://ubuntuforums.org/showthread.php?t=816825)

---

