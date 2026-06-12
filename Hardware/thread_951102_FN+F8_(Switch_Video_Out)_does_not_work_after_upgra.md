---
title: "FN+F8 (Switch Video Out) does not work after upgrading from 7.04 to 8.04"
date: 2008-10-17
forum: Hardware
---

### Post by FerhatBingol on 2008-10-17
Hi All,

I use Dell D620. It has Intel i810 chipset. XORG Gnome

Today I have upgraded to Ubuntu 8.04 previously I was using 7.04. 

In older version what I was doing;

1) Open the box with console mode
2) Press Fn+F8 and switch to my external monitor
3) update the video bios with 915resolution 5a 1600 x 1050 (to make it ready for my xorg.conf)
4) and STARTX to go in to XWindow

After the upgrade STEP 2 stopped working. Fn key works because I can play with the brightness for example, or any other Fn keys else than F7 or F8.

I tried to load keymap in console with 

```
loadkeys dk (I have a danish keyboard laptop)
```

but still Fn+F8 does not give the output to the external computer. 

Why my Fn+F8 does not work any more and how can I make it work?

Anybody to help?

Cheers,
f

P.S. Currently I managed to  use "displayconfig-gtk" and make EXTENTED screen to use my external monitor but I really do not need my laptop monitor. That is the reason I am trying to find a solution to boot my box on my external screen.

P.S.2 If you ask me why I do not just disable laptop monitor in "displayconfig-gtk" the answer is "in that case XORG does not start at all".

---

