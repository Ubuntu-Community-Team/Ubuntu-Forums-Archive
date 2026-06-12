---
title: "Does the video driver in Additional Drivers matter?"
date: 2015-10-04
forum: Hardware
---

### Post by cody27 on 2015-10-04
Just curious if the video driver you pick really matters or changes much.

I tried changing it from the first of the three to the second, and aside from the AMD Catalyst Control Center appearing in preferences I haven't actually noticed any difference. But is there something changing that I won't notice until I play a game or something?

I also noticed, both before and after changing the driver, that my screen seemed a bit...fuzzy, and at first I thought the resolution had changed but it's still the right one.
I dual-boot with Windows and my screen looks fine there so I'm not sure why everything seems like the wrong resolution in Ubuntu.

This is the first laptop I've had that actually has a choice of additional video drivers in Ubuntu so I have no idea if that's affecting anything.

EDIT: Here's the image of Additional Drivers. Forgot to add it the first time.
Also sorry for the large image. I'm not new to Ubuntu Forums, this is a new account because I lost my old email. But I can't remember if there's a way to hide images or make them smaller. I don't post too often.

[IMG]http://i.imgur.com/ddU5agF.png[/IMG]

Thanks!

---

### Post by dino99 on 2015-10-04
As you can see, Additional Drivers propose the available drivers for your card:
- first choice: the open source (aka radeon)
- then the closed ones: the most recent 'stable' and the latest one (updates)

its up to you to test which one works the best on that hardware.

---

### Post by cody27 on 2015-10-04
So one isn't less stable than the others?

Thanks, I'll make sure to switch between them and see what works the best.

---

### Post by mastablasta on 2015-10-05
there is /can be a difference between radeon and fglrx (closed ones) in OpenGL acceleration (games) and power management. fglrx usually is better. but not necessarily. and also sometimes it is only marginally better. this is because AMD is helping the guys doing the opensource drivers. I think long term solution is to maybe move to opensoruce or at least to move majority of the driver to opensource.

if you want to test it you can try glmark (this tests a bit older features so you might not see much difference) and then there is the phoronix test suite - you can try one of the engines tests (for example unigine) and see if there is any diference. but if you use it for desktop and don't have any power management issues (battery drain) then just leave them at opensource.

as for resolution and display you would need to explore what is causing it and then maybe there is some switch somewhere.

---

