---
title: "Laptop just shuts down"
date: 2012-08-27
forum: Hardware
---

### Post by atomicspin on 2012-08-27
I'm running Precise on a Toshiba laptop.  While booting up, it gets to a certain spot (before login) and the laptop just shuts down completely.  

I've been able to run memtest on the memory sticks with no errors.  Is there a way to slow down the boot so I can see what is loading when it crashes?  Do you know of another issue that might be causing this?

Thanks in advance.

---

### Post by Merrattic on 2012-08-27
Sounds like a kernel panic. You will need to boot in cli mode (3) or use the second line in grub for "recovery" to see where it goes pop, or check your logs from a live cd.

---

### Post by atomicspin on 2012-08-27
What log do I need to be looking at?  Trying to boot in recovery causes the same problem.  I'm logged in now via a Live CD, though.

---

### Post by atomicspin on 2012-08-27
Okay, I tried Lubuntu and Puppy Linux and it's the same problem, so it's not an OS issue.  

I've run memtest and it checks out just fine.  

What else could it be?

---

### Post by atomicspin on 2012-08-28
Looks like it was a bad power cord issue.  Sorry for the trouble.

---

