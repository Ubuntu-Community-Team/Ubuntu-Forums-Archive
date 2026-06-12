---
title: "Touchpad problem (Maybe more?)"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by ltracy on 2008-04-03
OK, I don't think there is a similar problem in other threads, but if I missed one, I apologize.

I am running Gutsy on a Dell Latitude D620.  For the most part I have had no problems, but since upgrading an issue has arisen.  At random times my touchpad will become unresonsive for a moment and then begin to work again.  After this unresponsive moment, my settings will be lost (i.e. acceleration and sensitivity are reset, tap to touch is re-enabled where as I have it disabled by default) and the preferences dialog no longer has any effect.  The following lines are quoted from dmesg

[ 8111.640000] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[ 8112.524000] psmouse.c: resync failed, issuing reconnect request
[ 8114.036000] input: PS/2 Mouse as /class/input/input17
[ 8114.056000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input18


I am wondering if this is something wrong with my hardware (i.e. is the touchpad actually disconnecting for some reason) or if this may be a software/driver issue.  Help would be greatly appreciated.

---

### Post by chewearn on 2008-04-03
I have the same laptop; don't have this problem.  But I installed Hardy since this week.  So, if it's a recent problem, like this week, then I don't know.

---

### Post by Iceman512 on 2008-04-03
That sometimes happened to me on my HP DV2550se and Gutsy. I too am running Hardy now and it hasn't happened once yet *knock on wood*

---

### Post by irish8890 on 2008-05-15
I have the same problem with Hardy losing glidepoint synchronization.  No solution yet.  Hopefully something get fixed so I don't have these frequent freezing episodes.

BTW, did you upgrade or install from scratch?  I went the upgrade route and am wondering if that is the reason for this issue.

John

---

### Post by ltracy on 2008-05-15
I had the problem on Gutsy after upgrading from Feisty (is that the right order?).  I did a scratch install of Hardy, and I don't believe I've had the problem since...  Although it doesn't make much sense to me why, maybe there's a correlation.

---

