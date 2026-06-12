---
title: "Please, please tell me how to configure CPUDYN :)"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by Zingam on 2005-05-30
Since powernowd does not work for my Mobile Pentium 4. I'm trying to install cpudyn but I can't get it to work. I also want the CPU freq scaling applet to show my frequency.

What should I do :) I'm not new to Unix but I'm new to installing Linux.

So far I have updated the kernel to 2.6.10 - 686-smp (I think this is the right kernel for MP4, isn't it), installed/compiled the latest ATI drivers form their web site.

Now I want to configure the CPU frequency scaling.  It hasn't to be cpudyn if it works somehow and I understand how to do it.

---

### Post by obiwan on 2005-07-10
I have a Mobile Pentium 4 and powernowd works with it. You just have to load a module to let the kernel access the cpu scaling functions. 

I loaded speedstep-ich for my Inspiron 5150:

$ sudo modprobe speedstep-ich

---

