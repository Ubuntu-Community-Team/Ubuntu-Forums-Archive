---
title: "X not displaying on laptop display unless external monitor plugged in (fglrx, T60)"
date: 2009-06-04
forum: Hardware
---

### Post by ck_ on 2009-06-04
Hello, 

please help me figure this behaviour out, I am completely lost on it:

If I power up my laptop while the power supply is plugged in (and the external monitor is disconnected), everything works normally, I see the framebuffer splashscreen and afterwards gdm.

When using no power supply, i.e. booting with battery power only, I see the splashscreen, but the display goes black as soon as X starts. Plugging in a monitor does not show a picture on either the laptop display or the monitor. Switching to a virtual console doesn't show anything.

When using no power supply but an external monitor, I see the splashscreen on that monitor, but gdm displays on the laptop display.

My laptop is a T60 with an ATI X1400, running ubuntu 8.10.
I'm using the fglrx driver.

Can anyone help me?

---

### Post by LepeKaname on 2009-06-18
You have a strange problem there... Maybe is related to "laptop mode" packages... I'm not sure, never heard about it. Try also to change your X11 driver at you xorg.conf from fglrx to "vesa". This way you can see if it is related or not... sorry I can't help more...

---

