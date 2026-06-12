---
title: "resolution and volume issues on latitude e5400..."
date: 2009-03-12
forum: Hardware
---

### Post by masavini on 2009-03-12
hi to everyboody,
i guess this is my first post (can't remember if i wrote something in the past).
i have ubuntu intrepid 8.10 on my dell latitude e5400.
after 1 months since i installed linux, i only have a couple of issues:

1) sometimes the window manager starts at 1440x900 (native resolution), sometimes it starts at 1024x768. when i write SOMETIMES, i really mean there is no way to understand why it changes the resolution. no apparent reason.

2) low volume. i know it's a common problem, but if someone could help, it would be great.

here is the output od hwinfo --short about the 2 devices (video and audio boards):

graphics card:
                    Intel Cantiga Integrated Graphics Controller
                    Intel Cantiga Integrated Graphics Controller
sound:
                    Intel 82801I (ICH9 Family) HD Audio Controller

here is my xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

if anyone could help me, it would be great.
thanks
matteo

---

### Post by mprada on 2009-07-22
Hi, I'm having exactly the same problems, have you managed to solved it.

In fact in my case it's worse, because since yesterday it ONLY boots with the wrong resolution. Now it's not just SOMETIMES. :(

---

### Post by cjfarley on 2009-12-09
I too am having problems with the display settings and can't seem to lock it down.  I have 15 laptops for a school that I want to install ubuntu on but I want to get this problem fixed first.  Anyone have ideas?

---

### Post by mprada on 2009-12-09
In my case the problem disappeared when I installed Ubuntu 9.10 (Karmic Koala). I'm afraid I've not delved into the problem any deeper.

---

### Post by masavini on 2010-07-10
bumping again...

problem solved with 9.04 -> 9.10 upgrade, but now with 10.04 the screen resolution issue is appeared again...

when i boot running on battery the resolution falls to 1024x768 (native is 1440x900), and the same happens after about 50% of screensaver resumes...

any idea of what has been changed in the screen resolution managing process? 9.10 was perfect...

---

