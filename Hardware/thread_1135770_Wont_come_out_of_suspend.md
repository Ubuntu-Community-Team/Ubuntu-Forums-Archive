---
title: "Wont come out of suspend"
date: 2009-04-24
forum: Hardware
---

### Post by riskyayush on 2009-04-24
Hi,
I am using Ubuntu Intrepid Ibex on a Toshiba Satellite L305 laptop.
The laptop seems to go in suspend mode nicely, but when I try to bring it back, the hard drive light glThe problem is that glows on indicating its got power, but the screen remains dark.
Please suggest how I can solve this issue.
Thanks

---

### Post by yoasif on 2009-04-24
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

please submit a bug report to [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug") with your issues.

---

### Post by riskyayush on 2009-04-24
1.dmesg:

wont let me paste the whole thing here

2. cat /proc/cmdline

root=UUID=998f0246-6b1a-4136-bec9-52d373c143b0 ro quiet splash 

3.cat /etc/initramfs-tools/conf.d/resume

cat: /etc/initramfs-tolls/conf.d/resume: No such file or director

---

