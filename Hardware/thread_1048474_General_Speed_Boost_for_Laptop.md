---
title: "General Speed Boost for Laptop"
date: 2009-01-23
forum: Hardware
---

### Post by icanfly0307 on 2009-01-23
Hi all, I have a 1Ghz Pentium III, 256MB RAM Vaio laptop. It runs decently but I was wondering if there were tweaks to get it to run even faster? I don't mean anything specific to Ubuntu. By "general", I mean something that will effect the computer's performance on the whole. Is this even possible? Thanks.

---

### Post by kerry_s on 2009-01-23
i wish i had 1ghz. :)
i got the vaio pcg-f430 450mhz 256mb ram. 
basically what you want to do is reduce the resources. the less running the more for other things.
also the suspend and hibernate work perfect, use them and save some boot time.
for full control a custom install is best, you just install what you use. choose a light window manager, pcmanfm is a good file manager, leafpad for simple text editing, etc...

i'm currently using arch linux, it does a base/core install and you build it up from there with what ever you want. jwm is my wm of choice, it's very light and flexible.

---

### Post by icanfly0307 on 2009-01-23
I can't get my X to work under Arch so no go there. BTW, I have a PCG-FX370. I'm guessing your lappy is from the previous series. :)

And would 1Ghz be really considered fast? Windows XP shows me 993Mhz instead of 1Ghz... :/

---

### Post by kerry_s on 2009-01-23
> **icanfly0307 said:**
> I can't get my X to work under Arch so no go there. BTW, I have a PCG-FX370. I'm guessing your lappy is from the previous series. :)

And would 1Ghz be really considered fast? Windows XP shows me 993Mhz instead of 1Ghz... :/

yeah, it's around 10 years old. 1ghz is enough for me, i could do wonders with it. :D

arch is a bit tricky, but if you follow the beginners guide it should work.
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

yours would be:
```
pacman -S libgl xorg xf86-input-evdev xf86-video-intel

```

the driver is the same as your using now in ubuntu.

---

### Post by iggykoopa on 2009-01-24
you could look into crunchbang linux, it's based off ubuntu but uses openbox.

---

