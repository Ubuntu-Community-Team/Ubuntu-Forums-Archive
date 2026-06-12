---
title: "Laptop Touchpad scroll rocker button crazyness"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by kevellis on 2007-11-19
Hi all for my first post.

After extensive googling I've been unable to get the scroll button under my touchpad working correctly.

The laptop is an Acer Aspire 7720 running a fresh install of Gutsy (Although It never worked under Feisty either)
The button I refer to is the scroll up/down rocker button beneath the touchpad and between the L/R click buttons.
Pressing UP on the button causes a downwards scroll.
Pressing DOWN causes any one of the following things to happen,

-Mouse pointer moves left by ~300 pixels
-Current window minimises
-Clipboard text is pasted
-Makes all touchpad buttons unresponsive

To be honest I don't really mind whether this button ends up as a scroll up/down button or just as a middle click. So long as I can get rid of the random crazyness I'll be happy.

---

### Post by kevellis on 2007-11-21
Bump!

Surely someone can at least point me in the right direction to start figuring this out?

Thanks.

---

### Post by kevellis on 2007-11-30
Bump!

HELP, I'm still getting nowhere.

---

### Post by CFath on 2008-01-15
I have an Acer laptop 5050 and my scroll button acts all funny as well.  I would like the button to work properly as I have gotten used to using it from the windows side of things.

---

### Post by kevellis on 2008-02-21
Any ideas anyone. I've got everything working perfectly now with this one exception.

---

### Post by kevellis on 2008-02-21
Okay, here's some more information I just figured out. Its an ALPS touchpad. Here's the output from cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0008 Version=7325
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input13
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=f
B: KEY=420 0 670000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

Does that get me any closer?

---

### Post by kevellis on 2008-02-27
After a little messing around I was able to make it work correctly on the Hardy Alpha 5 livecd.
I guess I'll just wait for Hardy.

---

### Post by MiataMuc on 2008-02-27
Hi, I managed to get my Alps-touchpad working by just changing the kernel for my Gutsy to the Hardy-kernel. There a thread here in the forum: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755) which made that easy for me. The problem - as far as I understand it - is, that the Alps-touchpads are not beeing recognised as Touchpad, and are only beeing used as PS/2 - mouse; the newer kernel recognises them correct.

Hope this helps,

Flo

---

### Post by CFath on 2008-03-18
So Hardy is due out in April???

---

### Post by kriekske on 2008-05-10
I've had the same problem. the button is recognised know but when I push up it scroll down and when I push down it scrolls up. Has someone a solution for this or the same problem? 
I've a Acer Aspire 7520G

---

