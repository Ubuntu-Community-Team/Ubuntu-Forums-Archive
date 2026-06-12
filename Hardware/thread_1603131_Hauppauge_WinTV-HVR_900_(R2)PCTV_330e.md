---
title: "Hauppauge WinTV-HVR 900 (R2)/PCTV 330e"
date: 2010-10-22
forum: Hardware
---

### Post by tomsimmons on 2010-10-22
Folks

A genius over Kernel Labs has managed to get these USB tuners working.

[http://www.kernellabs.com/blog/?p=1397&cpage=1#comments]("http://www.kernellabs.com/blog/?p=1397&cpage=1#comments")

As you can see from the comments it's working in most cases, looks to be working upto 10.04, sadly for 10.10 (which I'm on) there's a problem.

When you try and 'make' it you get the errors mentioned about kfree/kzalloc.  I have tried the fixes mentioned about adding the reference to linux/slab.h, makes no difference for me.

I'm afraid although I'm a programmer, I'm still finding my feet regarding Linux, so hopefully a genius here can give some guidance for the last step of getting this built for the 10.10 kernel.


Tom

---

### Post by PCNetSpec on 2011-03-14
See here:
[http://linuxforums.org.uk/linux-tips-tricks/pinnacle-hybrid-tv-tuner-pctv-330e-in-ubuntu-10-10-maverick/](http://linuxforums.org.uk/linux-tips-tricks/pinnacle-hybrid-tv-tuner-pctv-330e-in-ubuntu-10-10-maverick/)

---

