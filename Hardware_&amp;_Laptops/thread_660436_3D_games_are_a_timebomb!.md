---
title: "3D games are a timebomb!"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by thumbmaster021 on 2008-01-06
Hello!

I have a problem with my HP Pavillion zd8000 laptop.
I have installed Ubuntu 7.10, and I was pleasantly surprised that ALL my hardware worked out of box!  For my built in wireless card and 3D acceleration on my Mobility Radeon x600 I used the drivers from the Restricted Drivers Manager,  And all it good, except one thing.

Whenever I play a 3D game, be it OpenGL linux native game(like Armagetron), or playing World of Warcraft under Wine in Direct 3D mode or OpenGL mode, It crashes after a short period of time!(were talking 1 - 2 min).  Now, before it crashes I get good FPS in all my games(except WoW in DX mode, but thats expected).

I have tried installing the ATI Preparatory drivers from their site, no change.

EDIT:
Did I forget to mention that I have Compiz Running in the background with the 3D cube and such with no problem, thought this would be important!
Also, when I say crash, I mean the whole computer just shuts off instantly.

Im clueless on what this could be :confused: .

Any help is greatly appecated!

Computer Specs:
HP Pavilion zd8000
2gb RAM
2.8 GHz P4 Hyperthreading Enabled
Mobility Radeon x600

---

### Post by brennydoogles on 2008-01-06
could you try running armegatron from terminal? After it crashes, the terminal window should still be open, and there may be valuable information in the terminal. The other thing I would try is turning off your screensaver. I used to have problems with Tremulous (a native game from the repos) crashing whenever the screensaver was enabled, because it would try to activate while i was playing. Hope that helps!!

---

### Post by thumbmaster021 on 2008-01-06
Thanks for your help, but I guess I did not make myself clear, when I say the game crashes, I mean the whole computer just shuts off, no warning, nothing.  Just *POOF*!  Sorry for the mixup.

---

### Post by keithclark on 2008-01-07
> **thumbmaster021 said:**
> Thanks for your help, but I guess I did not make myself clear, when I say the game crashes, I mean the whole computer just shuts off, no warning, nothing.  Just *POOF*!  Sorry for the mixup.

I think your system is overheating.

Keith

---

### Post by zeller on 2008-01-07
I've posted similar distresses with my zd8000. Just now I tried to simply copy a cd and it instantly shut off.

How do we check if it's overheating?

I ran Warcraft III for years under windows and other 3D games without a snag.

Thumbmaster021: I didn't have luck with the restricted driver. Upon installing my laptop still shutoff instantly. And don't use Emerald either, it will kill it too.

I hope someone can figure this issue out. It really is becoming bothersome.

---

### Post by aj_ on 2008-01-08
Most laptops have built in fans that kick in as the cpu temperature increases. If your lappy's fans aren't doing so, then a few minutes of gaming will cause the cpu / gpu temp to reach critical point, and the system will shut down to prevent damage.

I have an hp lappy as well (one of those 17" monstrosities), and my fans are working just as they do in windows. As soon as the cpu temp exceeds 46C, the cpu fan will rev up and the temp will go down.

If you want to monitor your lappy's temps, do a search for lm-sensors.

---

### Post by the_blur on 2008-01-08
I have the exact same problem, 3d apps shut my system down and sometimes hose my video driver / xorg.conf.

I discovered this when alien arena hosed my video config. I cried a little bit, but now I'm ok. If anyone knows how to fix this I'd love to know. As it is, what I did was to fix my grub so it boots into windows by default, but it's not a solution that I like, but I like games more than I hate windows.

Could this be related to the fact that CPU scaling doesn't work on my laptop either? (or sleep or hibernate)

I have a ZD8000, Prescott 3.4 (!), 2G of ram (but the lappy only sees 1.5G for some reason) ATI Mobility X600.

---

