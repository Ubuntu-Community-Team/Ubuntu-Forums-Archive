---
title: "USB causes crashs"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by burgermann on 2006-06-15
Hi. Everytime I insert a usb device my whole system crashes and I can't shut it down by it self. This have never been a problem in any other distro but Dapper Drake.

Is there a way to load the usb controller or something? I have no idea where to look or begin :S

---

### Post by ~A~ on 2006-06-15
Same problem here. The EHCI-HCD nodule got messed up again.
befor you plug in your usb device do:
```

sudo rmmod ehci-hcd

```
Your usb device won't work at full speed without ehci-hcd but it won't crash you system.
Then recompile your kernel with the old ehci module \\:D/ ](*,)
It would be even better if someone knows an easy way to get usb2 working

---

### Post by burgermann on 2006-06-15
Hmm. Tried it, but it still crashes. Actually it's more like a gigantic lag. Every 30 seconds the systems respons for about one second on the keys I've pushed and the mouse strokes I've made.

---

### Post by ~A~ on 2006-06-15
if you can still type you can use dmesg in a terminal to see what causes the problem.

---

