---
title: "clock() runs slow"
date: 2011-12-06
forum: Hardware
---

### Post by glcoder on 2011-12-06
I'm using a Sony VAIO vpcyb15kx laptop and Ubuntu 11.10.

The time reported by the clock() function in C/C++ runs slow if I boot normally. It reports fine if I boot into recovery mode. The time() function that is based on seconds reports fine in either mode.

I tried:
- installing the proprietary ATI driver, which did not help.
- noapm noacpi noapic nolapic kernel options, which only served to make the system unbootable.
- maxcpus=1 kernel option, which did not help. I also tried setting the /sys/devices/system/cpu/cpu1/online file to contain the value of 0, which did not help either (no surprise).
- installing the indicator-cpufreq package and tried all governor / cpu frequency modes, which did not help (in fact, made it slower when I set it to max frequency and performance mode)

I am at a loss as to what to try next. I'd just boot and code in recovery mode, but I need the window manager and OpenGL for my application to fully run. Any ideas would be greatly appreciated. :-k

P.S. It is the following code that erroneously reports that 1 second has elapsed after about 2-3 actual seconds, but again, only after booting into the window manager. Works fine in recovery mode:

while(1) 
{ 
    float curr_time = static_cast<float>(clock())/static_cast<float>(CLOCKS_PER_SEC); 
    cout << curr_time << endl; 
}

---

### Post by glcoder on 2011-12-06
Sorry, make that:

maxcpus=1

That was a typo in the first post. Apologies for any confusion.

---

### Post by jmate24 on 2011-12-06
there is an edit button in your posts if you want to edit them.

---

### Post by glcoder on 2011-12-07
It was brought to my attention that the CPU time is not the wall time. I now use clock_gettime() instead of clock() on Linux. Works good.

Thanks for the tip on editing posts. :)

---

