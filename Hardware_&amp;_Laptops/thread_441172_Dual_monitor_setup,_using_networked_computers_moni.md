---
title: "Dual monitor setup, using networked computers monitor?"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by ebichu on 2007-05-12
Hi.
Can anyone guide me somewhere, please?!
I am trying to set up dual monitor thingy, on feisty, using other computers monitor over lan.
Not even trying yet, but searching for solution.
[http://www.maxivista.com/](http://www.maxivista.com/) << this is what i have in mind.
I think Synergy is not the right thing, because, if i understand correctly, it just like shares mouse and a keyboard, right?
So, pleasepleaseplease help me. : )

---

### Post by gg234 on 2007-05-29
try [this simple guide ]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html") to setup dual monitors

---

### Post by regomodo on 2007-06-27
> **gg234 said:**
> try [this simple guide ]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html") to setup dual monitors


you've totally misread what the OP is trying to do

Ebichu, i'm currently trying this with my laptop. You have to run it through Wine. I'll post back what i can

---

### Post by regomodo on 2007-06-27
Ok,

As far as i can tell you can only do this with the server on windows and the viewer in Linux(under Wine). You cannot do it fully under Linux.

What i did was install the server 1st on windows. I then created the viewer executable. This created .exe is run under wine on the 2nd computer. The 2nd computer creates a window, not full screen, where the 1st computer (server) can move in and out of. 

I had issues with my setup. It'll only run at High Picture quality configuration, otherwise the screen is a mess or doesn't work at all. It felt a little slow, possibly due to using an ancient laptop, but all mouse/key functions appeared to work.

I've attached a screenshot

---

### Post by bb7110 on 2007-08-01
I am trying to do the same thing, except my main laptop is 6.06 Dapper , and the laptop I want to be my second monitor is also a 6.06. Is there a Linux program that will do what I want? I have been playing with VNS, but I cannot figure out how to use it as a dual monitor, rather then just sharing my current screen.. Any ideas??

---

