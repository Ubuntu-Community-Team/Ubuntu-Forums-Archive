---
title: "Ubuntu and Rescue and Recovery in ThinkPad T61"
date: 2008-11-03
forum: Hardware
---

### Post by jingtian on 2008-11-03
Hi, after I installed Ubuntu 8.10, the Restore and Recovery function did not work in my ThinkPad T61 anymore.

I guess grub broke the hidden partition in ThinkPad, which is used for rescue and recovery.

How to solve this issue?

---

### Post by jingtian on 2008-11-12
I done some research on this topic, and now my question is: how to install GRUB into the Linux partition instead of MBR? Can anyone help?

---

### Post by turbowei on 2009-02-10
Bump.

Does anyone have answer to this???

I am in the same boat now. The rescue and recover doesn't work anymore. :(

---

### Post by era86 on 2009-02-11
Honestly, I think that partition is lost.  When you installed Ubuntu, did the partitioner show some space that was being used as R and R?  If you used the whole disk for Ubuntu, there is a good chance that partition was erased.

---

