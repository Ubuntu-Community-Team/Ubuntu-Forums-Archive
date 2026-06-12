---
title: "Only able to see and use one processor"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by alphaakenny1 on 2007-01-24
Hey I have a Dell Inspiron e1505 with a Core 2 Duo Processor T7200, unfortunately Ubuntu only sees one processor.  I am currently running Ubuntu 6.06 and was wondering if this is all it can use or if I can turn it on somehow.  Thanks in advance.

---

### Post by SendDerek on 2007-01-24
I had to install a i686 package of some sort... I'll go find it now.........

Here's the thread that worked for me.  I figured it would work for you as well!  Basically, it was said to install the linux-686-SMP package and it's dependancies and you'll be set!

Check your System Monitor before and after installation to see if it made a change!  It was pretty cool to see the system monitor come up with two processors once I restarted.

---

### Post by 454redhawk on 2007-01-25
> **alphaakenny1 said:**
> Hey I have a Dell Inspiron e1505 with a Core 2 Duo Processor T7200, unfortunately Ubuntu only sees one processor.  I am currently running Ubuntu 6.06 and was wondering if this is all it can use or if I can turn it on somehow.  Thanks in advance.

I think you have to install the generic kernel.

---

### Post by alphaakenny1 on 2007-01-25
What do you mean generic kernal?  I am a newb.

---

### Post by dabl on 2007-01-25
Here are the basics about kernals and the one you need for dual cpu:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

:)

---

