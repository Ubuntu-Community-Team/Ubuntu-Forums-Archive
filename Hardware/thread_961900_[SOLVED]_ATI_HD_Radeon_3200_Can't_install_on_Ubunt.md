---
title: "[SOLVED] ATI HD Radeon 3200 Can't install on Ubunt 8.10"
date: 2008-10-28
forum: Hardware
---

### Post by Izek on 2008-10-28
Running the run file results in...

```
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib::none:2.6.27-7-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.T10315
```

Using the x86_64 run installer. I know there is a [patch for it](http://www.phoronix.com/forums/showpost.php?p=48886&postcount=10), but how do I get the source, and when I have the source, how do I run it? Yes, I've been new to linux for more than 3 years. I asked on the phoronix forums, but the forum I posted in required moderator approval. *shudder even though that's a good thing*

---

### Post by Darthcolo on 2008-10-28
Had you tried the 32bit version?

---

### Post by Izek on 2008-10-28
> **Darthcolo said:**
> Had you tried the 32bit version?

x86 and x86_64 have the same catalyst installer in 8.10 for linux.

=========================

Solved:

installed xorg-driver-fglrx from the **Synaptic Package Manager**.

---

