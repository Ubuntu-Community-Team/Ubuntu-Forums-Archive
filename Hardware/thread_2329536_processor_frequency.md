---
title: "processor frequency"
date: 2016-07-02
forum: Hardware
---

### Post by mary72 on 2016-07-02
Hi, I wonder why there are so low frequencies if the nominal are 2.30GHz.
I installed hardinfo and it says about my CPU:

[IMG]https://s32.postimg.org/7k4dx8rs5/zrzut.png[/IMG]

Why is it so?

---

### Post by Linuxisfast on 2016-07-02
Thats normal, the intel_pstate driver modulates frequency as per system load and need.

---

### Post by efflandt on 2016-07-03
Intel Speedstep Technology, Example:```
efflandt@XPS-8100-1404:~$ grep MHz /proc/cpuinfo
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
efflandt@XPS-8100-1404:~$ glxgears &
[1] 5386
efflandt@XPS-8100-1404:~$ 56949 frames in 5.0 seconds = 11389.626 FPS
grep MHz /proc/cpuinfo60780 frames in 5.0 seconds = 12155.949 FPS

cpu MHz        : 3201.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
```Although, /proc/cpuinfo only shows max non-turbo speed. If your cpu is capable of turbo (which is automatic in Linux), to see actual turbo speed when your PC is doing something cpu intensive, you would need to install **i7z** and run that using **sudo** (sudo i7z).

---

### Post by mary72 on 2016-07-03
Thank you. :)

---

### Post by mörgæs on 2016-07-03
If the question has been answered please mark the thread 'solved'.

---

### Post by mary72 on 2016-07-03
Thank you for reminding, done

---

