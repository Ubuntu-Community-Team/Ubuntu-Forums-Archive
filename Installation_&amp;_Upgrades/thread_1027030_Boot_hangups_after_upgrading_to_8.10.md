---
title: "Boot hangups after upgrading to 8.10"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by zselek on 2008-12-31
Hi,

I am looking for a solution for the following problem:

After upgrading to 8.10 my system cannot boot with the 2.6.27-9 and the 2.6.27-7 kernels. It freezes completely when the progress bar reaches about 40%.
When running in recovery mode, it can be seen that the last action it does is:
Configuring network interfaces...

After that it only keeps writing "...BUG: soft lockup -CPU#0 stuck for 61s!..." every minute, and only a power-off helps.

However, the 2.6.24-14 kernel can boot up, but it also stops for 2 minutes at "Configuring network interfaces...", but after that it goes on normally. (Unfortunately the X server is very unstable with the 22-14 version, so using this kernel is not a real solution.)

Interestingly, in rare cases (usually after system upgrades) the 2.6.27-9 was able to boot up, but only once and by the next time the same problem came back. (The X server works fine with the 27-9 version, so reviving this one would be the optimal solution.)

Any help is appreciated!

Thanks!

---

### Post by xzero1 on 2009-01-01
This is probably a longshot, but since you have mentioned 'configuring network interfaces'; it caught my eye. You may want to examine an unresolved bug I filed a while back: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223893.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223893")

As mentioned, the problem was serendipitously corrected since I had to replace my router. A careful examination of your logs should indicate whether this bug applies.

---

### Post by zselek on 2009-01-01
I have attached the 3 log files that the bug report of xzero1 was referring to. (Note: it was made by the 2.6.22.14 kernel, since the newer ones cannot boot up.)

I do not think it is a router related problem, since it occurs also if the router is completely disconnected (both wired and wireless).

---

### Post by zselek on 2009-01-01
It seems that the attachments did not succeed, maybe this time...

---

### Post by xzero1 on 2009-01-03
You might want to examine the logs of a buggy kernel boot. After all, something is writing "...BUG: soft lockup..." to a log. There are a few things you can try. Remove the quiet and splash parameters from the kernel's boot command line via grub. Search the logs in /var/log for your bug message or boot with the live-cd to retrieve the old log. File a bug report adding the information you might gather.

---

