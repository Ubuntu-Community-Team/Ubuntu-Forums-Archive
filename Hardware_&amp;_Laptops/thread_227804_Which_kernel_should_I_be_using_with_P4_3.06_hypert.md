---
title: "Which kernel should I be using with P4 3.06 hyperthread?"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by cantormath on 2006-08-02
Does anyone know which kernel I should be running.  Currently im running kernel 2.6.15-26-386 #1 PREEMPT, this is the kernel I have installed and updated to.

my cpu is a PIV 3.06 hyperthread chip. 
my [hwinfo]("http://cantormath.com/hwinfo.txt") and [lshw]("http://cantormath.com/lshw.txt").

If there is any other info anyone needs to answer this, let me know.

---

### Post by jordilin on 2006-08-02
With hyperthreading you should use the **smp** one.

---

### Post by cantormath on 2006-08-02
> **jordilin said:**
> With hyperthreading you should use the **smp** one.

ok, thanx.
I have tried that kernel in the past....ie)
sudo apt-get install linux-686-smp

and for some reason it seems a little glitchy, do you have any suggestions on maybe optimizing the kernel for ones specific hardware.  If that is to general a question I can be more specific.  Again thanks.

---

### Post by jordilin on 2006-08-02
> **cantormath said:**
> ok, thanx.
I have tried that kernel in the past....ie)
sudo apt-get install linux-686-smp

and for some reason it seems a little glitchy, do you have any suggestions on maybe optimizing the kernel for ones specific hardware.  If that is to general a question I can be more specific.  Again thanks.

I have a PIV 3GHz hyperthreading and I have been using the smp kernel without problems. You can always tweak it but this is quite difficult and I wouldn't recommend it. In any case take a look at the following thread:
[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)

---

### Post by cantormath on 2006-08-02
> **jordilin said:**
> I have a PIV 3GHz hyperthreading and I have been using the smp kernel without problems. You can always tweak it but this is quite difficult and I wouldn't recommend it. In any case take a look at the following thread:
[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)

yeah, I really didnt have recompiling the kernel in mind.  I will give the smp a try.

---

