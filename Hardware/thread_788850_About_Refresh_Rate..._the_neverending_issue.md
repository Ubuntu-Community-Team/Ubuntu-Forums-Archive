---
title: "About Refresh Rate... the neverending issue"
date: 2008-05-10
forum: Hardware
---

### Post by samathyr on 2008-05-10
Hi!

This is my first post in this forum. I hesitated with Ubuntu, but after try it I am sooo happy :D 

The only thing I have been struggling with was the Refresh Rate of the Screen. I have been looking for more information about this, and I follow the indications explained in another post ( [http://ubuntuforums.org/archive/index.php/t-76387.html](http://ubuntuforums.org/archive/index.php/t-76387.html) )

I have an **_HP Pavilion CTO dv6000_** with a "***Nvidia GeForce Go 7200 TurboCache supporting 128MB***" and after an evening customizing by desktop my eyes were almost bleeding. Then, I realized that I was working with 50Hz.

I follow the instructions and I changed to 1280x800 @ 85.00 Hz (same resolution, more refresh rate) and I copy this in my xorg as root:

#```
 1280x800 @ 85.00 Hz (GTF) hsync: 71.40 kHz; pclk: 123.38 MHz
Modeline "1280x800_85.00"  123.38  1280 1368 1504 1728  800 801 804 840  -HSync +Vsync

```

Save and Restart

My doubt is very easy.
How do I know if the changes are really made?

I should perceive it, but just in case, I prefer to see it

If I click in System/Screen Resolution/ the Hz shown stills 50 Hz

pd: With this characteristics... how much Refresh Rate could I set safely?

Thanks!

---

### Post by samathyr on 2008-05-12
Up!

Please, I really want to know this.... I 'm concerned with my eye's health

---

### Post by timzak on 2008-05-12
What kind of monitor do you have?  LCD or CRT?  Most monitors will tell you the current refresh rate if you enter the monitor's menu (the buttons on the front of the monitor).  I'm not sure how LCD monitors work refresh rate (my understanding is that they all run at 60 Hz, but I could be wrong), but with CRT monitors, you generally don't want to go more than 85 Hz.  The higher the refresh rate, the more stable the image, but also, the image gets blurry and less vibrant with refresh rates that are TOO high.

Edit:  Just realized you're in the laptop subforum (I saw your post from the forum main screen without knowing what subforum it was in).  Maybe someone else can help, my understanding is there is no refresh rate configuration with LCDs and laptops, but I could be wrong.  Hopefully someone else chimes in.

---

### Post by samathyr on 2008-05-12
Thanks for your answer! :D

It is a LCD screen (we are talking about a laptop).

Before try with the xorg editing, during the start-up of Ubuntu the screen was a little bit blurry, but after a few seconds, it finally gets established. Now, that issue has disappeared, so I guess the new refresh rate is working. 

The problem is I don't know how can I visualize the actual refresh rate (no built-in menu, this is a laptop). My eyes are better than the first day... but I had not problems with Windows Vista Refresh rate settings, that's why I would like to know the optimal refresh rate for this laptop also. 

Thanks!

---

### Post by Zorael on 2008-05-12
The Nvidia driver is bugged and reports a lower refresh rate than it actually pushes out. So if it says 50hz, you're seeing 60hz.

LCD screens generally only want 60hz.

---

### Post by GnuSense on 2008-05-12
samathyr, you might look over at this article on the Perfect Hardy Desktop on HowToForge:
[http://howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p2]("http://howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p2")

It has some recommendations about font settings that may or may not be useful.

---

