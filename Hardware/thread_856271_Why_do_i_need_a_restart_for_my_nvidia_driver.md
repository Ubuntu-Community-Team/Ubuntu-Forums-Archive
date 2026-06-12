---
title: "Why do i need a restart for my nvidia driver?"
date: 2008-07-11
forum: Hardware
---

### Post by markg85 on 2008-07-11
Hey,

The question is simple.
Why do i need to restart my pc to get the nvidia driver working?

insmod nvidia and a X restart should be enough right!

So with that knowledge again: Why do i need a restart?
It's not modifying the kernel base kernel which is about the only thing that requeres a restart on linux and you can only get it that far if you install a new kernel or compile a new one.

My suggestion:
Kick out the restart demand and just restart X.

---

### Post by unoodles on 2008-07-11
Not sure exactly what is happening, but if you really think this is a good idea, you could post it over at brainstorm.ubuntu.com

---

### Post by markg85 on 2008-07-11
Great!! yet another ubuntu related registration needed
Gonna make that a "brainstorm" as well

Edit:
brainstorm for the thread:
[http://brainstorm.ubuntu.com/idea/11037/](http://brainstorm.ubuntu.com/idea/11037/)

---

### Post by sdennie on 2008-07-11
You don't need to restart if you know how to remove the old module and insert the new one.  The restart request is because Ubuntu tries to cater to everyone.  Putting a message up saying, "Stop X, remove the old module, insert the new one, and start X again" is beyond most people.  "Reboot" is fairly straightforward though.

---

### Post by markg85 on 2008-07-12
> **vor said:**
> You don't need to restart if you know how to remove the old module and insert the new one.  The restart request is because Ubuntu tries to cater to everyone.  Putting a message up saying, "Stop X, remove the old module, insert the new one, and start X again" is beyond most people.  "Reboot" is fairly straightforward though.

Your both right and wrong at the same time.
Your right in what you say. Yes.
The general idea is wrong. Ubuntu should take care of the insmod and rmmod if needed and ubuntu should tell the user something like:

"Click here to activate your new driver" which then restarts x.

---

### Post by L815 on 2008-07-12
> **markg85 said:**
> Your both right and wrong at the same time.
Your right in what you say. Yes.
The general idea is wrong. Ubuntu should take care of the insmod and rmmod if needed and ubuntu should tell the user something like:

"Click here to activate your new driver" which then restarts x.

But if Ubuntu is trying to target any audience with easy computing, not everyone know what X is...
Reboot IMO is straightforward and a common solution to many driver installations.

---

### Post by avam323 on 2008-07-12
> **markg85 said:**
> Your both right and wrong at the same time.
Your right in what you say. Yes.
The general idea is wrong. Ubuntu should take care of the insmod and rmmod if needed and ubuntu should tell the user something like:

"Click here to activate your new driver" which then restarts x.
this WOULD be the ultimate fix, but i don't think posting it here will get it to the folks who could make the change...

---

