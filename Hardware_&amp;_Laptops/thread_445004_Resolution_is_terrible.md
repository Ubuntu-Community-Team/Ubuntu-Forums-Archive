---
title: "Resolution is terrible"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2007-05-15
I hope someone can help me: I'm stuck at 640x480 resolution and it's terrible! 
I've recently installed Kubuntu 7.04 on an IBM desktop PC with a 82845G/GL [Brookdale G]/GE Chipset integrated graphics Device

Tungsten Graphics, Inc. 
Mesa DRI Intel (R) 845G 20061007 x86/MMX/SSE2
Open GL version 1.3 Mesa 6.5.2
Kernel Module i915 (I added this after)
My Monitor is a ViewSonic Ultrabrite E70f+

Anyway, I just want to have 1024x768 back. Can someone please help?

---

### Post by heimo on 2007-05-15
Have you seen this?
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by teejay17 on 2007-05-15
> **heimo said:**
> Have you seen this?
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Okay, I tried some of the suggestions at the very bottom--the one titled  "Well, it worked for me: Feisty, Intel i810"--and I completely broke my system. 
Now that I'm reinstalling Ubuntu (instead of Kubuntu) does anyone have any resolution tips?

---

### Post by taurus on 2007-05-15
Boot into recovery mode and reconfigure your X again.  Use i810 as the driver for your Intel graphic card.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by teejay17 on 2007-05-15
> **taurus said:**
> Boot into recovery mode and reconfigure your X again.  Use i810 as the driver for your Intel graphic card.

```
dpkg-reconfigure xserver-xorg
```
I did. It seems that I was able to reset my resolution properly...it looked great...I was so excited that I pulled it off. The problem was my machine kept rebooting every ten seconds or so...continually...over and over again. 
This gave me the impression that something was definitely broken.

---

### Post by teejay17 on 2007-05-15
Now that I have Ubuntu installed, will it be easier to fix this resolution problem? I can go back at a later time and install KDE on the system, and right now I just want to get my resolution displaying properly. 
Right now it's so terrible, I can't even see the top, bottom, nor either side of any window that is open. My screen real estate is even more compromised in Ubuntu, having two bars taking up space. 
Like I've mentioned above, before my system broke, I tried getting my resolution to display by following instructions at the link provided. 
That didn't work. 
There must be a plan B.

---

### Post by teejay17 on 2007-05-15
Of course, I should mention that right now, before anything gets done, I have a fresh install of Ubuntu 7.04 with no updates/installs/or anything yet. 
Don't know if this will make a difference, but maybe it will...

---

