---
title: "CPU I/O Wait at 100%, stays that way"
date: 2008-08-06
forum: General Help
---

### Post by Jackelope on 2008-08-06
I'm running Hardy on an Intel Centrino laptop. Now and then it will show 100% cpu usage in the system monitor task bar applet (the one on the panel) for no apparent reason. More specifically, the I/O Wait gauge is at 100% cpu but the System gauge is only at 12% or so. When I check the actual system monitor application it reads 12% cpu usage, but the applet is still showing 100% and the computer is sluggish. This usually happens when running firefox or synaptic, but neither of them should be maxing out my cpu. I think I need to reduce the amount of I/O Wait somehow, but its just a guess. Sometimes the processor recovers and sometimes it gets so sluggish I can't even move the mouse or restart X. Any idea what could be causing this? Fixes? Thanks ahead of time for any help!

---

### Post by tamoneya on 2008-08-07
next time you see this happening can you please close the system monitor in the panel and run```
top
``` in terminal.  system monitor isnt very accurate because it actually put a non-negligible load on the CPU.  Top however does do this.  It will also provide more information about the system.

When you run top it will update every second or so.  We just need to see one "frame".

---

### Post by RealPSL on 2008-08-07
The I/O Wait is the amount of time your CPU is spending processing I/O. This means something is either doing a lot of hard disk activity or you have a slow disk device. It also includes other input/output devices as well but most times it is related to hard disk usage. The hard disk is generally the slowest part of the computer so any big activity there will make your computer feel slow.

---

### Post by Jackelope on 2008-08-08
Thanks for the explanation, Real. I've been doing a bit of research on it and the hard disk slowing things up makes a bit more sense than the CPU causing problems. Next time it happens (I can't seem to force it) I'll try running 'top' and see if I can get more detail.

---

