---
title: "ATI Radeon 9800 PRO Drivers"
date: 2009-10-10
forum: Hardware
---

### Post by zoff_ita on 2009-10-10
Hello,
ATI Catalyst propertary driver doesn't support ATI Radeon 9800 PRO anymore...
There would be no problem if Legacy driver would work fine but it isn't...

On my PC ATI Legacy drivers sucks...
Even if:
```
$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (R350 4E48) 20090101 AGP 8x x86/MMX/SSE2 TCL

```
...even a simple action like scroll web-pages is laggy...

So, my question is:
Must I return to Ubuntu 8.04, give up and keep this nasty legacy driver or what else?

Hoping for good news,
- Zoff -

---

### Post by DemonioFlatline on 2009-11-19
I have the same problem.

Any suggestions?

---

### Post by cutterjohn on 2009-11-19
ATI seems to be pushing people below R600 GPUs to their open source driver, BUT I'm not sure how the 3D support is for older cards, but it may be worth trying.  (I know that 3D support for R600 and newer GPUs isn't all that good ATM, and one of the devs said a few months ago something like a year until they're decent. 2D support is supposed to be fine already.  Just as an additional re-inforcement these comments apply to R600 and newer GPUs which is what I was interested in as it directly applies to mine, RV770 -- 4850 mobility.)

Otherwise you COULD run 9.04 and up to catalyst 9.3(.4?) IIRC which was around when they dropped the older cards.

---

### Post by zoff_ita on 2009-11-19
> **cutterjohn said:**
> ATI seems to be pushing people below R600 GPUs to their open source driver, BUT I'm not sure how the 3D support is for older cards, but it may be worth trying.  (I know that 3D support for R600 and newer GPUs isn't all that good ATM, and one of the devs said a few months ago something like a year until they're decent. 2D support is supposed to be fine already.  Just as an additional re-inforcement these comments apply to R600 and newer GPUs which is what I was interested in as it directly applies to mine, RV770 -- 4850 mobility.)

Otherwise you COULD run 9.04 and up to catalyst 9.3(.4?) IIRC which was around when they dropped the older cards.

9.3 driver isn't compatible with jaunty kernel...
I should use intrepid and in that case I'll prefer the LTS...
This is why I wrote about hardy in my message...

---

### Post by bailout on 2009-11-26
I am having problems with kubuntu 9.10 and my 9800 pro. Very laggy when moving or resizing windows and when anything is redrawing windows. I didn't have similar problems running ubuntu 9.04 and may go back to it myself when I get time.

---

### Post by DRF on 2010-02-02
Regarding the poor performance it might be worth checking that you're not experiencing the effects of bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413)

There appears to be some issues loading the opensource radeon driver that some people are experiencing so you may find you lack any 3D acceleration (eg compiz etc).

Daniel

---

### Post by cobratbq on 2010-05-08
I have the same problem. I have not found a solution yet, but I'll keep checking this thread.

---

### Post by zoff_ita on 2010-05-09
> **cobratbq said:**
> I have the same problem. I have not found a solution yet, but I'll keep checking this thread.

ATM I workarounded the problem installing latest kernel from Xorg-edgers PPA.

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

---

