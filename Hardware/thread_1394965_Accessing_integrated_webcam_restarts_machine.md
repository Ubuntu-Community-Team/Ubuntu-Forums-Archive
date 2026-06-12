---
title: "Accessing integrated webcam restarts machine"
date: 2010-01-31
forum: Hardware
---

### Post by kcamarda on 2010-01-31
I have an HP Pavilion dv6 laptop with Ubuntu 9.10 installed.  When I try to access the integrated HP Webcam, e.g. with cheese, my computer reboots. Does anyone have an idea as to what's going on?

Thanks.

Karen

---

### Post by kcamarda on 2010-01-31
I'm sorry - I seem to have figured it out, and can't figure out how to delete my post.

The problem was that a few months ago, when I was installing 9.10, I added "i915.modetest=0" to my boot command to address the bug described at [https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/+bug/431812](https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/+bug/431812) . It was supposed to be "i915.modeset=0". (Strangely, my version seemed to fix the problem...)

---

