---
title: "NVIDIA GTX 660M with prime: tearing and screen refresh issues"
date: 2016-04-20
forum: Hardware
---

### Post by geenux2 on 2016-04-20
Hi everyone,
I know several topics exist on tearing with NVIDIA, and even bug reports on the nvidia tracker.
Yet I haven't been able to find so much as a workaround, and my issue seems to be worse than most posts
show.

Whenever I have an external monitor plugged in, one of the screen (either my laptop's or the external monitor)
experiences serious refresh issues:
- Most of the time, only parts of the screen where I move the mouse are refreshed.
There are also often ghosting effects, where the mouse cursor trail remains on screen (ie several pointers).
- Huge tearing often appears as well.
This makes using multiple screen impossible.

I am using:
- NVIDIA GTX 660M with nvidia-364, 364.15, kernel 3.19.0-58-generic, x86_64   (from ppa:graphics-drivers/ppa)
- NVIDIA prime. This laptop is used for work, and I use and develop GPU-intensive applications permanently, 
thus bumblebee is not an option.

My Xorg.conf is the default one, I was under the impression that there was no reason to alter this file anymore.

A common point in most posts related to the issue is to add this to the xinitrc (or lightdm)
> xrandr --setprovideroutputsource modesetting NVIDIA-0
This only results in a black screen for me.

Did anyone experience similar issues? Any ideas on any workaround?
Thanks in advance for your help.

---

