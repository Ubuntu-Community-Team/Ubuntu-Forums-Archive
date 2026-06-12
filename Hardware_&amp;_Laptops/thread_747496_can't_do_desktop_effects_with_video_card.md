---
title: "can't do desktop effects with video card"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by dragonmm2010 on 2008-04-06
[CENTER][SIZE=4]hi all plz i want help i have fujitsu siemens 3515 laptop
 
and i try alot to install ubuntu 7.10 and i can't

today i already install 8.04 on my lap top but i can't

make the effects plz i want how to make ubuntu make this effects in my lap to

my video card is via chrome 9

can i found anyone help me how to make ubuntu make the 3d effects on this driver[/SIZE]
[/CENTER]

---

### Post by SunnyRabbiera on 2008-04-06
well firstly slow down!
secondly Hardy is still a beta and Gusty is unstable (in my opinion anyway)
you may have to hold out on hardy, give it a few weeks and it will be stable but right now its still in beta.

---

### Post by Crafty Kisses on 2008-04-06
Yeah, not sure what the problem is, but did you actually get into Ubuntu, because you said you tried to install Ubuntu and it didn't work, then you say you're trying to get your Video card drivers installed, I'm confused.

---

### Post by sdennie on 2008-04-06
I don't know that your video card is supported for desktop effects.  You could check that by doing the following from a terminal:

```

glxinfo | grep -i texture_from_pixmap

```

If that command comes back with no information I don't think you can use desktop effects.

---

### Post by dragonmm2010 on 2008-04-06
[LEFT]i tried to install ubuntu 7.10 and faild on my laptop 
and yesterday i downloaded ubuntu beta 8.04 and this time i installed ubuntu on my laptop 

now my video card ubuntu can't know it i want to make ubuntu know my video card and make 3d effects 

my video card is 

via chrome9 

that i have on fujitsu siemens 3515 


[/LEFT]

---

### Post by dragonmm2010 on 2008-04-06
up want help can anyone help me in this problem

---

### Post by futsihoo on 2008-05-30
tried to let desktop effects work for over a year now, starting from Ubuntu 6.10 on the same fs laptop. never succeeded. only recently updated to 8.04, but have no hopes it will work, unless someone on the forums has a bright insight. I'll keep on looking :)

~$ glxinfo | grep -i texture_from_pixmap
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by dragonmm2010 on 2008-05-30
I found the soulation and worked for me 

**[how to install via on ubuntu]("http://arabicubuntusupport.wordpress.com/2008/05/15/how-to-install-via-on-ubuntu/")**



and also about the brightness from here 

**[brightness in ubuntu]("http://arabicubuntusupport.wordpress.com/2008/05/17/brightness-in-ubuntu/")**



and if desktop effects worked but u will may found proplem in the video u can found the soulation here 

**[how to fix video in compiz]("http://arabicubuntusupport.wordpress.com/2008/05/18/%d8%ad%d9%84-%d9%85%d8%b4%d9%83%d9%84%d8%a9-%d8%a7%d9%84%d9%81%d9%8a%d8%af%d9%8a%d9%88-%d9%81%d9%8a-%d8%a7%d9%84%d9%83%d9%85%d9%88%d8%a8%d9%8a%d8%b2-how-to-fix-video-in-compiz/")**

---

