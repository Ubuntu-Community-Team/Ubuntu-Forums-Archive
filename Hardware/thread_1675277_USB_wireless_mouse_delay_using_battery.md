---
title: "USB wireless mouse delay using battery"
date: 2011-01-25
forum: Hardware
---

### Post by demian85 on 2011-01-25
When i use the laptop without ac power mouse works perfectly, but when using battery, after 5 seconds of inactivity or so, the mouse does not respond instantly, i have to move it like 5 seconds or so... it happened with a microsoft usb wireless and now i have a brand new logitech with usb nano receiver. same problem!
what can i do?
thanks.

pd: using ubuntu 10.10 on a Samsung R480 laptop.

---

### Post by demian85 on 2011-01-26
nothing? am i the only one?

---

### Post by demian85 on 2011-01-29
hi i'm having the same issue and nobody can help me!

---

### Post by demian85 on 2011-02-12
hello.

---

### Post by facelikebambi on 2011-04-30
Exactly the same here, using Samsung N210 Netbook, Logitech wireless USB mouse and Ubuntu 11.04.

Works fine on AC power but mouse movement lags intermittently every few seconds. Seriously annoying! #-o

---

### Post by Moi meme on 2011-05-10
Look like problem.

Since I installed Ubuntu 11, my usb mouse stop working on battry only.

But if I unplug and plug the mouse, they work only if I don't stop moving the mouse.

When I stop mouving the mouse, I cannot use it again until I unplug and plug it again, or if I plug the power to the laptop.

I thing the problem begin after I install laptop-mode-tool, or some battery monitor or stat tool.

---

### Post by steing on 2011-05-10
Try setting 
CONTROL_USB_AUTOSUSPEND=0
in /etc/laptop-mode/conf.d/usb-autosuspend.conf.

---

### Post by Grillmeister on 2011-06-03
Thank you so much, you just saved my day.
Didn't realize at all, that I installed laptop-mode-tools and was wondering why usb-mouse AND -keyboard were freezing instantly after unplugging power cable.

Now everything works fine again.

---

### Post by rimez on 2011-07-04
I think this thread can be set to [solved]. The suggestion worked for me as well. Thanks for that :)

---

