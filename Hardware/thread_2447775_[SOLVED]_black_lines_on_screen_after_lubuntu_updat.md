---
title: "[SOLVED] black lines on screen after lubuntu update on old ThinkPad"
date: 2020-07-25
forum: Hardware
---

### Post by gino2490 on 2020-07-25
On my old ThinkPad t42p  with Lubuntu 18.04.2 x386 and ati firegl mobility T2 (M10) video card, strange black lines are appeared after the weekly update. They are thin and on all the screen. 
I have reinstall lubuntu from dvd and the screen looks good. But the lines reappear after the new update. They're in logon window and desktop and all other windows. They cover images and words and it's difficult to read.
Please don't tell me "it's time to buy a new PC". let's do it to others companies.
I have tried:
New installation of Lubuntu 18.04.2 from dvd 1 year old-: all works fine. After updates black lines reappear
New installation of Kubuntu 18.04.4 from dvd 1 year old: all works fine. After updates logon window has black lines and desktop is completely black 
Change screen resolution to lower don't goes better.
Dummy solution:
In standard normal mode Radeon driver is set as autodetec driver 0, ATI driver as autodetect driver 1.
In recovery mode, that works all fine, ati driver is autodetec as driver 0.
So I start with recovery mode and select the first "resume to normal boot". In this way ati driver is selected. I don't know if the video driver is the reason why, but in this way it works.
True solution:
Install with nomodeset option

---

