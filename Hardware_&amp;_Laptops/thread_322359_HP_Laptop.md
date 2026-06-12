---
title: "HP Laptop"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by RocketManKeith on 2006-12-20
I am trying to  install Ubuntu on an older HP Pavilion N5150 laptop with no success. The Ubuntu desktop tries to come up but in the end I am left with a blank orange colored screen. I suspect that there is a video issue here but I am a newbie to this. Any ideas? The laptop is an Intel P3 with 128MB RAM and a 40G HDD.

---

### Post by nsleiman on 2006-12-20
did u succeed in installing ubuntu? if no try to install it first in normal text mode! it can be your graphic card.
If u got it installed try to log on to the console and edit /etc/X11/xorg.conf there is a line about the graphic card driver.

---

### Post by DarkN00b on 2006-12-20
Most definitely use the alternate install cd to install Ubuntu. The liveCD requires 256 MB of memory to run in graphical mode. Even then it runs slowly.

---

### Post by meng on 2006-12-20
With 128MB, you may even want to use the Xubuntu alternate CD rather than the Ubuntu alternate CD, since Xfce is lighter than GNOME. GNOME may still be okay though.

---

### Post by sophtpaw on 2006-12-20
> **RocketManKeith said:**
> I am trying to  install Ubuntu on an older HP Pavilion N5150 laptop with no success. The Ubuntu desktop tries to come up but in the end I am left with a blank orange colored screen. I suspect that there is a video issue here but I am a newbie to this. Any ideas? The laptop is an Intel P3 with 128MB RAM and a 40G HDD.

from what i can tell its all about the video card with linux and laptops. But you've alredy intuited this. You need to tell people what your graphics card is

---

### Post by Sef on 2006-12-21
> I am trying to install Ubuntu on an older HP Pavilion N5150 laptop with no success. The Ubuntu desktop tries to come up but in the end I am left with a blank orange colored screen. I suspect that there is a video issue here but I am a newbie to this. Any ideas? The laptop is an Intel P3 with 128MB RAM and a 40G HDD.
Edit/Delete Message

I second the use of [Xubuntu]("http://xubuntu.org").  I have a Dell Laptop with 700 MHz processor and 128 mb ram.   Ubuntu needs 256 mb ram minimum, so it barely worked if I could get it to work.   [Xubuntu]("http://xubuntu.org") needs 64 mb ram, so on my laptop it works real well.

---

### Post by vincentvee on 2006-12-28
> **RocketManKeith said:**
> I am trying to  install Ubuntu on an older HP Pavilion N5150 laptop with no success. The Ubuntu desktop tries to come up but in the end I am left with a blank orange colored screen. I suspect that there is a video issue here but I am a newbie to this. Any ideas? The laptop is an Intel P3 with 128MB RAM and a 40G HDD.
i had that same problem with mine, i had to install 5.10 as a text install, then upgrade to 6.06 using the live cd and dist upgrade
there are several howto's here that i had to sort of blend together, i didn't document exactly how i did it, but i'm sure you'll find one or two that will tell you everthing you need to know

---

