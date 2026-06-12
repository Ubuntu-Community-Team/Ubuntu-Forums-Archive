---
title: "Slow down during power connection"
date: 2012-02-06
forum: Hardware
---

### Post by majikins on 2012-02-06
Hi

I have a Dell E5420 and have recently bought myself a 9 cell battery for it.  Everytime I plug in the power, my mouse cursor becomes slow to respond and some applications as well such as the file explorer - some files take a long time to list etc. As soon as I unplug the power cord, every thing changes back to normal.  Does anyone have any pointers/solutions?

M

More info: I notice my CPU increases processing from 1% to 10-15% for a while when power is plugged in. The slowness also seems to be random sometimes. When I wake the laptop from suspension, there is still a bit to charge but everything is back to normal again.  But when slow and I reboot, even at logon screen, the mouse drags.

HELP!

---

### Post by michu162 on 2012-02-08
I've got the same issue with my E5420.
Ubuntu 11.10
Linux lap 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux

Can anyone help?

---

### Post by majikins on 2012-02-13
Ok after a bit more digging, when I plug in the power, a process called kworker kicks off and consumes CPU.  More digging around got me this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793)
and
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717919](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717919)

Seems to a bug in the latest kernels with no obvious solution yet.

---

### Post by chicken159 on 2012-03-17
Add one to the E5420 go-slow on plugging in the power supply....anyone find any solution?

---

### Post by michu162 on 2012-03-19
Try 
echo N> /sys/module/drm_kms_helper/parameters/poll
as root


It helps me

---

### Post by chicken159 on 2012-03-20
There's a bunch of threads on this issue, and there is a temporary and a permanent fix.

The previous post provides a temporary solution, ie.
echo N> /sys/module/drm_kms_helper/parameters/poll

To make this a permanent solution, create/edit /etc/modprobe.d/local.conf  to add the following line:

options drm_kms_helper poll=N

Then restart and the problem should go away.

---

### Post by majikins on 2012-04-02
Kudos chicken159!

That worked for me.

---

### Post by wandalalakers on 2012-04-15
I have an E5420 also.  I applied this fix and hope that it works for me.  Thx Chicken!

---

