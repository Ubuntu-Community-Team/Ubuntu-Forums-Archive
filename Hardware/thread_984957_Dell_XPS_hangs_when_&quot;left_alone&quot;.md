---
title: "Dell XPS hangs when &quot;left alone&quot;"
date: 2008-11-17
forum: Hardware
---

### Post by ildella on 2008-11-17
Hi all. 

I am using a Dell XPS 1530, nvidia soundcard, with Ubuntu Intrepid Ibex on it. 
I installed ubuntu Gutsy around january, the dev versione, and update after update, here I am. 

The problem is: sometimes laptop hangs on completely. Freezed, no answer, no input works, nothing. The two front light on the laptop start blinking and the computer is gone. There is only hard shut down by keeping the button presseed for a few seconds. 

This kind of freeze never happens when I am using the laptop but when I left it alone, it freezes almost every times. 

I guess is something related to ACPI and suspend. I have configured it to never suspend anything (disk, monitor... nothing), but the laptotp continue to freeze after some minutes of inactivity. 

The same kind of freeze also happens sometimes when I am listening to music with VLC or Elisa or sometimes also with Movie Player. 

This is the onoly problem I have. It is very very rare that the PC hangs on in onother situation or that simply some application crash bring with him the whole system. This to say: the system is stable but for this problem. 

Any idea? some ACPI log to look at?

Thanks.

---

### Post by linux_tech on 2008-11-17
Anything in the log files, how about output of dmesg?

---

### Post by damis648 on 2008-11-17
Try Ctrl+Alt+F1 and log in there. Then leave it alone, and see if any output is shown when it freezes. I have an m1530 and have never experienced anything like this.

---

### Post by ildella on 2008-11-17
> **linux_tech said:**
> Anything in the log files, how about output of dmesg?

I will check next time, but I need some tips: dmesg show output without any time reference, how can I find the lines for the eventual crash?

---

### Post by ildella on 2008-11-17
> **damis648 said:**
> Try Ctrl+Alt+F1 and log in there. Then leave it alone, and see if any output is shown when it freezes. I have an m1530 and have never experienced anything like this.

I will try. 

I have done this test in the last hour: left it alone without skype, firefox and AWN, just with pidgin and a terminal session opened. 

System did not crash. 

Skype is my number one sucpected.

---

### Post by Nixie Pixel on 2008-11-17
Is your problem similar to the one found in [this thread?]("http://ubuntuforums.org/showthread.php?t=976287")

---

### Post by ildella on 2008-11-17
> **Nixie Pixel said:**
> Is your problem similar to the one found in [this thread?]("http://ubuntuforums.org/showthread.php?t=976287")

looks the same, I start following the other thread. 

Thanks.

---

### Post by rampras on 2008-12-08
Try the solution mentioned here:
[http://www.megalinux.net/solution-dell-xps-m1530-ubuntu-810-system-freeze-issue/](http://www.megalinux.net/solution-dell-xps-m1530-ubuntu-810-system-freeze-issue/)

I had faced a similar issue and that solved it.

---

