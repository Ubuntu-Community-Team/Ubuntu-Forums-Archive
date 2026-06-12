---
title: "What is my cpu speed?"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by skorange on 2006-02-20
Hi, recently installed kubuntu on my Averatec 3225 laptop.  It has an Athlon XP-M 2000 (approximately 1.5GHz) processsor.  According to KInfoCenter, it is running at around 400 MHz.  Presumably, it must be in some throttle mode.  How can I verify this?  How can make sure that the throttling is working/is installed correctly for my hardware setup so that it goes up to full speed when it needs to?

Thanks~
Stephen

---

### Post by spartas on 2006-02-21
try 

```

cat /proc/cpuinfo | grep -i Mhz

```

from a Konsole

---

### Post by skorange on 2006-02-21
here's /proc/cpuinfo: ```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : mobile AMD Athlon(tm) XP-M (LV) 2000+
stepping        : 0
cpu MHz         : 398.115
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips        : 786.32
```

and as you can see, it is at 400 MHz.  What makes throttling possible?  That is, is there some package or module that determines this?

---

### Post by crd on 2006-02-21
There's a great tutorial on powernow (Gentoo, but applies easily to Ubuntu) at
[http://gentoo-wiki.com/HOWTO_PowerNow!]("http://gentoo-wiki.com/HOWTO_PowerNow!")

If you're just trying to kick up the MHz to see if the throttling is working, open up two terminal windows.  In one, run the following:
*cat /dev/urandom > /dev/null*

In the other, watch the data in /proc/cpuinfo, and it should very quickly show a higher MHz (or bogomips).  The other window is hammering the cpu with operations, so make sure to Ctrl+C to kill it when you're done checking the cpuinfo.

crd

---

### Post by skorange on 2006-02-21
crd,

thanks!  that was very informative :)  it appears to be working correctly, bumping up the processor up to max speed!  I'll definitely check out the howto.
Stephen

---

