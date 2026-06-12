---
title: "High Memory Freeze"
date: 2008-10-01
forum: General Help
---

### Post by Ocxic on 2008-10-01
I've recently installed Ubuntu 8.04 64-bit on my dad's computer, and so far everything is great, with one exception. 

When using the computer, the memory will eventually fill up,, All being used by programs (dark green in the system monitor) when this happens the computer will freeze (become unresponsive, but still running) and I have to shutdown the computer to get is working again. (this includes swap, it will fill the same way just after the memory maxes out) 

This is especially prevalent when running VirtualBox, when it allocates the memory required to run windows, Memory will max out, system will freeze up for a few minutes, VirtualBox aborts mamory is released, and things are back to normal.

I'd really like to get this functioning normaly so that my dad can stop rebooting his machine into Windows and I can finally get rid of the dual boot.
This is my final obstical

---

### Post by spiderbatdad on 2008-10-01
not sure what to recommend on this...linux uses memory to cache data for faster performance. I'm wondering if your swap is large enough...also considering you are having a problem while running virtual machine...I remember a couple of years ago having to fiddle around with a thing called swappiness...I haven't used a vm for a while...maybe edit /etc/sysctl.conf...set swappiness:
```
vm.swappiness=100
```

---

### Post by Ocxic on 2008-10-01
This happens even with swap turned off. and I've tried changing that setting as well

---

