---
title: "Fujitsu Laptop p8010 brightness problem"
date: 2008-07-16
forum: Hardware
---

### Post by sunscape on 2008-07-16
Over the past few months I have asked in forums all over the internet about how to make the brightness controls (Fn + F6 and F7) work with my laptop and I got no responses. So, i tried compiling the latest kernel (2.6.26) and suddenly my laptop started recognizing the keycodes for the Fn key combinations in xev. Good news!

The problem is that gnome responds to the key combinations and pretends to change the brightness accordingly with the little meter shown in the middle of the screen, however, nothing actually happens.

Does anyone know what steps to take next to make it work?

---

### Post by nexx on 2008-08-31
I have a brand new fujitsu A6120 laptop and also cannot use Fn-F6 or Fn-F7 to dim my screen.
As a partial solution I installed xbacklight, a command line program that adjust my laptop luminosity.

  xbacklight -set 100

if you yant your screen at 100%.

Otherwise I was obliged to boot with vista to ajust the screen luminosity and then reboot ubuntu. May be something to do with the bios ????:confused:

---

### Post by darthbushi on 2008-10-21
It works for me! :guitar: Thank you, Nexx, for this solution. I was wondering, do you think it's possible to write a script to run xbacklight whenever we use Fn+F6/F7?

I'm a total n00b, so I'm only guessing here...

Thanks again! :)

---

