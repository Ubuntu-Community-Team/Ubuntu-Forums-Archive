---
title: "How do I stop the Power light blinking while in suspend"
date: 2009-12-12
forum: Hardware
---

### Post by uMuppet on 2009-12-12
When I close my laptop lid it goes into suspend mode (or sleep, not sure) when I open the lid and hit a key it springs to life almost instantly which is great, but can I turn off that annoying power LED blinking while its asleep?

I'm using 9.10 x86

Thanks

---

### Post by sliketymo on 2009-12-12
pull out the battery,or unplug.Use hibernate.Saves battery juice.

---

### Post by lisati on 2009-12-12
I suspect the behaviour the OP has observed is normal.

My laptop has a "sleep" mode. When powered up, the power light is a constant blue; when in sleep mode it flashes slowly in orange.

---

### Post by sliketymo on 2009-12-12
Yes,I am aware of that.My desktop does the same thing in sleep mode.You are correct.that is how it normaly works.OP asked how to stop it.

---

### Post by mtbsoft on 2009-12-13
I doubt you can stop it, it's almost certainly a hardware feature since all laptops I've seen that implement a suspend mode (irrespective of O/S) do something the same.  The O/S isn't doing anything at that point (it's SUSPENDed) and has simply called on the hardware to perform a suspend.

Frankly, I can't see why you'd want to do it, it's clearly there as a warning that your laptop is still in a state where it's consuming power and could potentially lose data if the power fails (i.e. battery runs out).

---

