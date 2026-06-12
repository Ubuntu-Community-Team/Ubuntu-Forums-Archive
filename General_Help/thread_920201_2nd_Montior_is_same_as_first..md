---
title: "2nd Montior is same as first."
date: 2008-09-15
forum: General Help
---

### Post by Mb0742 on 2008-09-15
Hey I just received my own 22" monitor. But the problem is, it refuses to play nice with my second one. Without the clone monitor option on in screen resolution is still copies what's on my lcd to the pixel. I want my lcd to be my first and my second monitor to act as a second one. 

Please can someone help.

Enclosed is my xorg server with was fixed by recovery mode.

---

### Post by lswest on 2008-09-15
Can you post information about your graphics card and driver you're using?  If it's nvidia (running the envy driver or the restricted driver), download and install nvidia-settings if you haven't already, then check the screen settings there.

---

### Post by Mb0742 on 2008-09-15
Almost there! It's all good now minus one problem, Thanks to the above post! I now can't get the second monitor out of 640X[(whatever)] res. In the nvidia setting it only shows that and 320 by something. And If I go to advanced and type in my own res it doesn't seems to have any effect.

[Once again I have enclosed my xorg.conf

---

### Post by lswest on 2008-09-15
> **Mb0742 said:**
> Almost there! It's all good now minus one problem, Thanks to the above post! I now can't get the second monitor out of 640X[(whatever)] res. In the nvidia setting it only shows that and 320 by something. And If I go to advanced and type in my own res it doesn't seems to have any effect.

[Once again I have enclosed my xorg.conf

This is mainly intended as a bump, since I've had a similar issue with my Intrepid installs, but I'm not sure how I fixed it (I did so many things, it could be any one of them or all of them).  Thanks for the thanks and I'm glad I was able to help you out in one aspect at least.  Maybe check the screen resolutions program in Ubuntu to see if you can change the resolution there, otherwise what I did was basically play with the resolutions in xorg.conf to see if it works (back up your xorg.conf before editing it at all, and I DO NOT recommend this approach to anyone, as it messed things up pretty badly and gave me a hard time getting the rest of the stuff working again).

Hopefully someone will post here with a solution

---

### Post by Mb0742 on 2008-09-15
[img]http://www.ricesigns.com/real_pictures/bump_signs.jpg[/img]

---

### Post by TheLions on 2008-09-15
try this one:

put this in terminal:

```
gksudo displayconfig-gtk
```

and press on display 2 and there choose option "second display"

like this:
[IMG]http://www.imagesforme.com/out.php/i156228_Prikazzaslona.png[/IMG]

---

