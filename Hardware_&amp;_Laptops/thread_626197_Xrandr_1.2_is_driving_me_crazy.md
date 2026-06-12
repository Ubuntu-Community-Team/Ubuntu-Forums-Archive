---
title: "Xrandr 1.2 is driving me crazy"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by 11touche on 2007-11-28
Okay, I want to set up my dual-head (dual-screen) under Gutsy. I've been able to do it twice, with xrandr 1.2, but now it just doesn't work anymore. Why? Dunno. Here's what I did to make it work with my ATI Radeon 9600XT, open source ATI driver:
first of all, I have the "virtual 2048x768" line in my xorg.conf under Subsection "DISPLAY"

```
 xrandr --output DVI-0 --off xrandr --output VGA-0 --off ;
xrandr --fb 1024x768 ;
xrandr --fb 2048x768 ;
xrandr --output DVI-0 --mode 1024x768 --left-of VGA-0 --output VGA-0 --mode 1024x768 ;

```
And all this used to work. But I just rebooted my system, and guess what, the exact same commands, which worked before, now don't. And I didn't do any updates. All I get is the same image, from the second screen (because I can't see the toolbars) and the DVI-0 monitor is in a yellow mood (like if there was no more red, only a blend of green and blue)
I tried several other commands, like enabling monitors one by one, but no luck. And it's not like if I couldn't because this morning, I was watching a video on my second screen while I was surfing on the net on the first one. So my question isn't "how can I achieve this?" but more like, why the heck isn't it working anymore?
I'm really pis*** off about Gutsy and this new Xorg + Xrandr
If anyone knows a way to get back Feisty's Xorg server without re-installing, it would be great since I kept my old (working) xorg.conf from it.

---

### Post by jis on 2007-11-30
I agree that setting video mode can be confusing in ubuntu 7.10, but I have good experience of xrandr with intel driver once I found instructions in internet. It is confusing when you don't know whether you should edit xorg.conf, use the Screens and Graphics preferences dialog or xrandr which is not well documented in gutsy in my experience.

---

