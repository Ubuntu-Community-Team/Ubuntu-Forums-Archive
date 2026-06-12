---
title: "Is my processor 64 bit?"
date: 2009-03-24
forum: Hardware
---

### Post by Open-SuSe-A-Me on 2009-03-24
Hi quick question.  I am finding conflicting reports online as to whether the "Intel Pentium Dual Core Mobile T2390"  (2X 1.86 GHZ) is 64 bit 32 bit only.

Anyone know for sure if this is 64 bit, and if i can install Ubuntu 64 bit version?

Thanks!

---

### Post by KCG102282 on 2009-03-24
Yes it is 64bit

---

### Post by Open-SuSe-A-Me on 2009-03-24
Thanks! just wanted to make sure.

Also, i have read that this processor is "low end" for a dual core.

will that effect 64 bit performance?

i have 32 bit right now and the performance is great.

Thanks!

---

### Post by Maheriano on 2009-03-24
Not sure if there were any 32 bit dual cores made.

---

### Post by kpatz on 2009-03-24
The original Core Duo CPUs were dual core and 32-bit only.

The T2390 supports 64-bit (EM64T on Intel's site).

Easiest way to find out for sure is to download a 64-bit 'Buntu iso, burn a Live CD and boot from it.  If it boots, your CPU supports 64-bit.  If it doesn't, you'll get an error to that effect.

---

### Post by stchman on 2009-03-24
> **Open-SuSe-A-Me said:**
> Hi quick question.  I am finding conflicting reports online as to whether the "Intel Pentium Dual Core Mobile T2390"  (2X 1.86 GHZ) is 64 bit 32 bit only.

Anyone know for sure if this is 64 bit, and if i can install Ubuntu 64 bit version?

Thanks!

If your processor was not and you tried to run the 64 bit Ubuntu via LiveCD, it will tell you the processor architecture does not support 64 bit.

---

### Post by jespdj on 2009-03-24
Intel's Processorfinder says [about the T2390](http://processorfinder.intel.com/details.aspx?sSpec=SLA4H) that it supports EM64T, which means that yes, it does have the 64-bit extensions.
> **kpatz said:**
> Easiest way to find out for sure is to download a 64-bit 'Buntu iso, burn a Live CD and boot from it.  If it boots, your CPU supports 64-bit.  If it doesn't, you'll get an error to that effect.
Yes, but maybe you don't want to download 700 MB and burn a CD and only then find out that it doesn't work...

---

### Post by hockeyhead019 on 2009-03-24
> **jespdj said:**
> Yes, but maybe you don't want to download 700 MB and burn a CD and only then find out that it doesn't work...

i agree with ^^^ haha

but really there isn't a huge advantage to going from 32 bit to 64 bit so if it's not broke don't fix it haha especially if you're newer to the system because many packages aren't as simple to install in the 64 bit version... but ultimately your call

---

### Post by Open-SuSe-A-Me on 2009-03-24
Thanks, I'm gonna give it a try.  I've been using Linux for a year and a half or so, and this will be my first experience with any 64 bit os.

---

