---
title: "Logitech MX Revolution"
date: 2009-05-10
forum: Hardware
---

### Post by jbo5112 on 2009-05-10
I have a Logitech MX Revolution, and recently switched from Gentoo to Kubuntu 9.04.  I've installed btnx, run btnx-config to enable revoco in free-scroll mode (the whole reason for upgrading my 10 year old mouse), manually started the btnx service, and manually restarted it, but I still can't use the middle butten.  Whenever I try, it still switches back and forth between free-scroll and click-to-click mode.  Being a software engineer and a systems engineer, I use the terminal excessively (highlight to copy and middle click to paste) and middle click in Firefox excessively, so this is about the fastest way to wreck my computing experience.

Have I left something out that I'm supposed to do with btnx?  Is this a bug in btnx?  Do I need to install something else to enable the revoco support?  Do I need to manually install revoco and roll my own init script?  I don't want to read through the 123 pages of the btnx thread.

---

### Post by jbo5112 on 2009-05-11
Any ideas?

---

### Post by mustang on 2009-05-18
As far as I know, BTNX stopped working after 8.10. I don't think it's been fixed to support 9.04 either. We're more or less out of luck.

---

### Post by jbo5112 on 2009-05-20
For now I've downloaded and compiled revoco.  I just run it manually when I need to.  I had been using Gentoo for years, and that's all I was using there.  If I use xev to figure out what the mouse buttons are, I can bind them to actions in Compiz, which is what I wanted the buttons for anyway.    It's sort of good to know that the program is broken, and that I'm not incompetent.

I seem to be running into a lot of intermittent bugs with Kubuntu 9.04 and KDE 4.2.  Hopefully 9.10 will fix a lot of them, as I'm still running 4.2.2 instead of the newly released 4.2.3.

---

### Post by mustang on 2009-05-21
thanks jbo5112. I was unaware of this program until now. Hopefully something more user friendly arrives in the future but this certainly works for now.

---

### Post by manca on 2009-05-24
I also manually compiled revoco and it works like charm... even btnx works good in jaunty :)

---

