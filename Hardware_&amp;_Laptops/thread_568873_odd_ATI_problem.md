---
title: "odd ATI problem"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by chaosmachine06 on 2007-10-06
Well, in trying to solve this issue I'm pretty sure it isnt a problem with ubuntu, but I'm afraid this is the only comunity I know of that might possibly give me an awnser. =p

I first installed kubuntu onto a maching with an ATI 1600 graphics card, when setting up the machine I decided to go with envy to lazily try to setup my card, it all went fine until I rebooted my system where no graphics came up, the screen was just dark, completely black, nothing.

So to see if it would work, I did the same time with an XP insall, this time useing the graphics card strait from ATI's website. I got the same exact thing, no diffrence at all. I rebooted when the instructions demanded it, and the screen was just black. I can however boot into safe mode with no problems.

Any suggestions?

---

### Post by elliotjreed on 2007-10-06
I've only had problems with envy. Try using fglrx instead.

To correct your dark/blank screen, try:

```
sudo dpkg-reconfigure xserver-xorg
```

...in the terminal, select your card type, resolution, etc.

---

