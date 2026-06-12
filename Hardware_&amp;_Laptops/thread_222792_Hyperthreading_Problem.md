---
title: "Hyperthreading Problem"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by Nibiruet on 2006-07-25
I am using a P4 3.2GHz CPU  which has Hyperthreading with 2GB RAM.

However, when Ubuntu 6.0.6 runs through the boot process I see a message that Hyperthreading is turned off though BIOS shows it as being on.

Kernel version is 2.6.15-26-686
GNOME version is 2.14.2 - Ubuntu (2006-06-15)
GCC version is 4.0.3 - i486-linux-gnu 
Xorg version is 7.0.0

Any way I can check **_after bootup_** if Hyperthreading is actually functioning?

---

### Post by Jagot on 2006-07-25
To check after bootup if it is running go to System -> Admin -> System Monitor.

Now go to the resources tab.  If it states that you have 2 CPU's then it's working, if not then it isn't.  The default kernel supplied with Ubuntu does not support HyperThreading - you need the SMP kernel.  If you have not installed it, then do this:

```
sudo aptitude update && sudo aptitude install linux-686-smp
```

Then restart.

---

### Post by Nibiruet on 2006-07-25
> **Jagot said:**
> To check after bootup if it is running go to System -> Admin -> System Monitor.

Now go to the resources tab.  It it states that you have 2 CPU's then it's working, if not then it isn't.  The default kernel supplied with Ubuntu does not support HyperThreading - you need the SMP kernel.  If you have not installed it, then do this:

```
sudo aptitude update && sudo aptitude install linux-686-smp
```

The restart.

Thanks. Found 2 CPUs. Also had installed v 2.6.15.26-686 SMP version.

---

### Post by wpshooter on 2006-07-25
I had been running the 2 of my machines that have hyperthreading with it turn off in the BIOS when I was running M/S.

If I turn it on now in BIOS, what would I have to do (same as above ?) to get it to show 2 processors and I wonder if this would allow me to run 2 instances of folding-at-home (perhaps a question for their forum) ?

Thanks.

---

### Post by Jagot on 2006-07-25
Yep - same as above to get 2 processors showing.  Fraid I don't know about the folding-at-home thing - Hyperthreading really isn't that impressive so I think you'd get quite a performance hit doing it, even with HT turned on.

---

