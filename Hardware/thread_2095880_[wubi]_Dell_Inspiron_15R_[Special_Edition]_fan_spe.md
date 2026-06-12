---
title: "[wubi] Dell Inspiron 15R [Special Edition] fan speed + temperature problem"
date: 2012-12-18
forum: Hardware
---

### Post by r4fay on 2012-12-18
I have a Dell Inspiron 15R SE ([click here]("http://www.dell.com/us/p/inspiron-15r-se-7520/pd") for details). I have installed Ubuntu 12.10 via Wubi on it. The OS works perfectly fine, but there are some issues:

[LIST]
[*]The fan speed is so high that it is actually audible. This doesn't happens when working with Windows 7.
[*]The laptop gets somewhat hot. Again, not an issue with Windows 7.
[*]Instead of showing me the name of my ATI graphics card, it shows "standard" or "generic" display drivers. (Pardon me, I cannot recall the exact name.)
[*]The battery drains twice as fast as it does on Windows 7.
[/LIST]
Other than the problems I have mentioned above, it works really good. No issue on software side at all.

---

### Post by ozp on 2013-01-28
hello my friend. Were you able to solve those problems? I got a Inspiron 15R today and it will arrive in 15 days.  I've read many reports like yours. Now the problem got even worse because new 15R comes with windows 8! (the most crap S.O. ever)

---

### Post by Mark Phelps on 2013-01-29
All of those are related to bugs in recent Linux kernels that prevent the CPU from automatically throttling back when idle -- a problem not affecting Windows because it uses an entirely different OS kernel.

That causes the CPU to run hot, overheating the PC, and wears out the battery sooner because it is not throttling back.

In some cases, installing the AMD drivers will allow you to control the GPU speed and temps -- giving some relief.

You can also look around for Jupiter -- which has also helped but does so by forcibly slowing down the CPU.

---

