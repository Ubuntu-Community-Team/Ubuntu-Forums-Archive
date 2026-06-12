---
title: "100% CPU utilisation"
date: 2010-02-12
forum: Hardware
---

### Post by Choragos on 2010-02-12
I had an interesting problem today.  Today I installed all the relevant scalapack libraries.  I compiled some [fortran] code using open mp.  I also copied the libiomp5.so file into my /lib directory so it would be in a pathed directory.  Somewhere in this process, my CPU usage went to 100% and stayed there.  No processes were listed that would explain this.  The problem was pervasive through several reboots.  Booted into Windows and my processors were not being used to 100%.  Booted back and they were again at 100%.  After a while, the problem took care of itself (maybe Ubuntu saw that I was searching forums for the answers to all my questions?).  I have not been able yet to recreate the problem.  Any thoughts?  Some system details are below.

Thanks!

9.10 Karmic Ubuntu
Kernel -19
Intel Core 2 Quad (2.83 GHz)
Compiled with Intel 64 bit fortran compiler

---

### Post by Scunizi on 2010-02-12
Perhaps the system was automatically looking for security updates in the background... and installing?  just a thought.

---

### Post by Choragos on 2010-02-12
I usually get asked.  Wouldn't that show up as a running process though (in the system monitor)?

---

### Post by Scunizi on 2010-02-12
Only if you have system monitor tagged to show all processes or system processes instead of user processes.. should be a menu option.

---

### Post by Choragos on 2010-02-12
Ah ha!  You da man.  That was it--thanks!

---

