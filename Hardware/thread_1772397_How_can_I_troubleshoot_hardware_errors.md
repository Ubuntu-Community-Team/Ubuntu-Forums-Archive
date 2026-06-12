---
title: "How can I troubleshoot hardware errors?"
date: 2011-05-31
forum: Hardware
---

### Post by achelis on 2011-05-31
Hi

I'm having an issue with my machine freezing and I suspect it might be a hardware issue since it sometimes freezes during boot even before Grub, BIOS etc.

I've been running Memtestx86+ which completed with no errors.

I'm wondering if there are similar tools for testing other hardware components, ie. my graphics card?

Or somewhere to find some log file which could give a hint towards what's wrong?

All help appreciated :)

---

### Post by jerrrys on 2011-05-31
what do ya got?  maybe a laptop with a bad battery or power supply

---

### Post by achelis on 2011-05-31
A PC. That is - not a laptop, so no batteries. This doesn't rule out the possibility of a faulty PSU though. I'd just like to be able to test before I go out and buy new components - else it could get very costly :)

---

### Post by psusi on 2011-05-31
How long did you let the memtest run for?  It needs to go for at least an hour.

When you have problems during or just after boot, is that after a reboot, or after the machine has been off for some time?

---

### Post by jerrrys on 2011-05-31
that would be a good guess. a weak PSU.

---

### Post by Rubi1200 on 2011-05-31
You could also check the logs for gaps or other information that might indicate a problem:

```
dmesg | less
```

Another possibility is to install bootchart and use that to troubleshoot issues:
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by achelis on 2011-05-31
> **psusi said:**
> How long did you let the memtest run for?  It needs to go for at least an hour.

When you have problems during or just after boot, is that after a reboot, or after the machine has been off for some time?

Will give it a try for a few hours - just gave it one pass.

During boot it's after a cold boot - rebooting a few times solves the problem. Else it's usually while playing certain games.

I reduced the RAM clockspeed a while back btw and that seemed to help.

My PSU has plenty of power to drive the hardware, but of course it could still have an error.

Would I have to run dmesg just after rebooting from a crash ?

---

### Post by achelis on 2011-06-01
Well, tried memtest for 1 hour and 15 minutes. Still no errors.

I'm still wondering about dmesg - I guess I should Google it :) - but if someone beats me to posting a link or description of how to use it for finding hardware errors you shall be very welcome!

---

### Post by psusi on 2011-06-01
Running dmesg after the crash will show the kernel log... after the crash, which isn't very useful.

---

### Post by marios88 on 2011-06-01
dmesg is the way to go

---

### Post by psusi on 2011-06-01
> **marios88 said:**
> dmesg is the way to go

Check again.

---

