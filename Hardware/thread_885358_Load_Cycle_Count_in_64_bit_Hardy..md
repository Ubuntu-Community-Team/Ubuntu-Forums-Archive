---
title: "Load_Cycle_Count in 64 bit Hardy."
date: 2008-08-10
forum: Hardware
---

### Post by stchman on 2008-08-10
Hello all.

Back in June 6th of this year I looked at the Load_Cycle_Count and it was approximately 4400.  I looked at it today and it is up to 26993.

Now the increase was not until I upgraded to 64 bit.  Does 64 bit handle this differently?

Thanks.

---

### Post by stchman on 2008-08-10
I think I found the fix.

I had changed my CONCURRENCY=none to CONCURRENCY=shell in /etc/init.d/rc a while back as some folks said that it is a better setting for a dual core processor.  I changed it back and the count appears to be ticking up at a slower rate.

---

### Post by stchman on 2008-08-11
That seemed to not fix the problem, the count is going up at a pretty good rate.

I still have a hard time believing that the hard drive is spinning down and up and parking the head that many times an hour.  I have put my ear down to the drive on the laptop and cannot "hear" it spin up or down.  Is this a 64 bit anomaly?

Please help.

Thanks.

---

### Post by Daelyn on 2008-08-12
> **stchman said:**
> That seemed to not fix the problem, the count is going up at a pretty good rate.

I still have a hard time believing that the hard drive is spinning down and up and parking the head that many times an hour.  I have put my ear down to the drive on the laptop and cannot "hear" it spin up or down.  Is this a 64 bit anomaly?

Please help.

Thanks.

There are countless, and countless, and countless threads about the "Load Cycle Count" in Ubuntu. I suggest you search for some solutions/fixes. There is also a "sticky" thread in the top of this forum named: ```
"[all variants] laptop harddrive Load_Cycle_Count issue ( 1 2 3 ... Last Page)"
```

---

