---
title: "OpenGL seemingly not done (Intel GMA 950)"
date: 2008-08-20
forum: Hardware
---

### Post by pteri498 on 2008-08-20
My computer, which I bought last November, uses the Intel Graphics Media Accelerator 950 chip (as advertised on the front sticker).

lspci tells me this:

```
$ lspci | grep Graphic
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

Compiz/desktop compositing/etc seem to work fine. However, when I come near anything that requires OpenGL (Google Earth), the system slows to a crawl. ZSNES won't even display in OpenGL mode. It's as if there's no hardware acceleration.

I can't imagine the chip is THAT bad, I have a 4-year-old ATI chip that handles things much better than this.

Is this a driver issue? Should I be looking into a new card?

Thank you.

---

### Post by pteri498 on 2008-08-20
This does not bode well for Ubuntu on my system:

I tried Google Earth in Vista, and it runs flawlessly. So smoothly does it run. I so very much want this in Ubuntu.

I updated the Intel drivers (xserver-xorg-video-intel) to the Debian Sid (Unstable) versions, and yet it only proves to be more glitchy than its predecessor (which is why I guess it's understandably called "Unstable).

Is there a 3D option I have turned off somewhere in Ubuntu?

---

### Post by pteri498 on 2008-08-20
```
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2

```

Direct rendering is on... what gives?

---

### Post by diwolfio on 2008-08-28
I'm having the exact same problem, no solution found yet. Google Earth is extremely choppy and not really worth using at this point. I know this doesn't help, but it's mainly just a bump.

---

### Post by Elessor on 2008-11-06
Had the same problem and after some digging discovered that Google Earth works fine after you turn off the "Atmosphere" option on the view menu.  Haven't found a fix as of yet.

---

### Post by VonSpyder on 2011-09-13
Sadly ubuntu and intel support for intels GMA950 is woefully lacking. There is no proprietary driver, and while there is an opensource driver it speaks nothing of this cards ability to use opengl or anykind of acceleration. Ive gone through Lucid, Maverick, and Natty and still nothing with what is the most prevalent video card for netbooks...which is really kinda irritating. Sadly this is why I keep my netbook as a duel boot.

---

