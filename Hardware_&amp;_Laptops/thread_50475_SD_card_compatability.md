---
title: "SD card compatability?"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by ibanez88 on 2005-07-20
I know this has been asked before, specifically here
[http://ubuntuforums.org/showthread.php?t=8381](http://ubuntuforums.org/showthread.php?t=8381)

however it doesn't appear to have been resolved and I'm having a similar issue.

I'm using an Averatec AV1050-EB1 with linux-686 v 2.6.10-7

From what I've read SD support is included in this version, however I can't get Ubuntu to recognize built-in SD reader.  Literally nothing happens when I plug it in..

dmesg shows no hde device, only hda and hdc

lshal | grep hd
lshal | grep SD or sd 
...show the same results

Any thoughts?

---

### Post by oobe on 2005-07-21
I found this driver and I'm pretty sure it's the right one, however I don't know how to patch the kernel, and nobody replied. This thread has the links.. 

[http://ubuntuforums.org/showthread.php?t=48551&highlight=oobe](http://ubuntuforums.org/showthread.php?t=48551&highlight=oobe)

oobe

---

### Post by ibanez88 on 2005-07-21
Thanks oobe.  I've never patched a kernel before either.  I'll give it a shot when I can, and will report success / failure.

---

