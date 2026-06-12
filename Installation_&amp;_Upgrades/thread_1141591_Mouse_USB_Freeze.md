---
title: "Mouse USB Freeze"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by cbweb on 2009-04-28
Hi,

I gave up trying to install Ubuntu following attempts at many workarounds to persistent mouse freeze problem, these occurred shortly after starting Ubuntu following new install.

So new install of xbuntu....Seemed to work OK for a while, but problem has returned with same severity as before. Mouse can freeze suddenly eg scrolling a web form.

Appreciate any suggestions. I wonder do I need new Linux drivers for the mouse on my Dell pc?

In BIOS I've enabled ON for all usb and usb controller settings?

Is there a possible disc error causing these, if what's the cure?

thanks

Colm

---

### Post by save2 on 2013-03-22
Asus M3N78-xxxx and family has a known issue with Ubuntu and freezing (mainly when attaching a USB device).

the symptom is that if you

run cat /proc/interrupts
you will some usb device raise 1000 interrupts/sec. maybe more.
I'm still looking for the solution.

---

### Post by oldos2er on 2013-03-22
Old thread closed.

---

