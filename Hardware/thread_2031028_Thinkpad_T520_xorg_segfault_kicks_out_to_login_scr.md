---
title: "Thinkpad T520 xorg segfault: kicks out to login screen"
date: 2012-07-21
forum: Hardware
---

### Post by iveand on 2012-07-21
Every few days after waking from suspend, my Lenovo Thinkpad T520 (Intel graphics) will operate for a few minutes and then randomly go blank for a few seconds followed by showing up at the login screen.

I looked in dmesg and found the following entry at the end:

```
[23710.271916] Xorg[1213]: segfault at 9 ip b7652b28 sp bff29560 error 4 in Xorg[b7532000+1f3000]
```

Any advice on what else to hunt down to get more info would be appreciated!

I did see something on askubuntu regarding an "error 4 in Xorg" with a Thinkpad x220, which was supposedly solved by disabling compiz.  I am not sure how to confirm whether I have a compiz problem or not.  No custom tweaks there (except for grid drag to top edge auto maximize is disabled and a few of the unity tweaks).

This is with Ubuntu 12.04.  All updates are applied.

Thanks,

iveand

---

### Post by Mitten O on 2012-07-26
I have the same problem.
I am using ubuntu 12.04 on an Asus Aspire One 532h.

Often, but not always when I return from suspension, the screen hangs for a moment
and then switches to the login screen.

The system tells me there has been an error and the details reveal Xorg crashed.
There is also a message in dmesg, which is essentially the same as the poster's above: segfault at 9, error 4 in Xorg.

The /var/log/Xorg.log indicates the segfault originated in XIChangeDeviceProperty+0x1b8
(or at least that is the only line in the backtrace that is more than numbers
before (vdso)__kernel_rt_sigreturn, which I assume is already a system error).

The problem appeared fairly recently, but due to it's random nature, it is difficult to
evaluate exactly when. I can definitely say it did not exist two months ago.

The last wo message in the log before the backtrace are:
SynPS/2 Synaptics touchpad found.
XKB: reuse xkmfile /var/lib/xkb/server-(bunch of numbers).xkm

I am sending this from another machine so sorry I couldn't copy paste the exact
texts. I am willing to do that if this information is not sufficient.

---

### Post by iveand on 2012-07-26
There is a bug on Launchpad for this issue.  Here is the link:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1026777](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1026777)

Unfortunately this is on my wife's "new" Thinkpad T520 so it isn't getting me any "bonus points" for converting her away from OSX/Macbook as it is her first Ubuntu machine.

As noted in the bug report, I can consistently get it to kick me out to the login screen if I do 3 consecutive suspend / wakeups (using either 2D or 3D).

---

### Post by 2F4U on 2012-07-26
I would suggest that you add your information to the bug report. This certainly increases chances that the bug will be fixed.

---

