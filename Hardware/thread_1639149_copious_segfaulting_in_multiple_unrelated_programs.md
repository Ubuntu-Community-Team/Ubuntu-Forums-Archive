---
title: "copious segfaulting in multiple unrelated programs"
date: 2010-12-06
forum: Hardware
---

### Post by deconstrained on 2010-12-06
EDIT: a while ago I got a new mainboard/memory. Segfaults and crashing stopped. Problem solved.

I've been experiencing crash after lockup after crash in Ubuntu 10.10, each accompanied by telltale segfault entries in the kernel log. Problem is, I've run memtest86 multiple times on my memory/cache and have not yet detected any memory problems, and I am not using any unusual settings in BIOS. The segfaulting always occurs when the CPU (a rather new Athlon II 640) is under at least a 30% load, i.e. when multitasking. The segfaults I've seen have thus far all been:

```
... error 14 in libfontconfig.so.1.4.4
... error 4 in python2.6
... error 6 in libavcodec.so.52.72.2
... error 4 in libflashplayer.so
... error 4 in libgstflump3dec.so
```
Furthermore, I've in repeated instances caused my system to lock up when running the program stress to test its stability, and find this in the kernel log:
```
... BUG: Bad page state in process stress
```
I've run into similar crashes before, but my system logs don't go back very far, so those events have all been as recent as the past three days. Can someone please point me to where I can learn what these error codes mean? 

I absolutely must diagnose this problem because it's taking a significant toll on my productivity. The crashing and lockups have been irritating me like nothing else I can remember in my history of using computers. I hope it's not a hardware issue but I'm prepared to hear that answer and would appreciate any and all opinions and suggestions.

---

