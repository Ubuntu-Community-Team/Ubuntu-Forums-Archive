---
title: "solution for kworker/kslowd problem?"
date: 2011-07-04
forum: Hardware
---

### Post by rooiwyn on 2011-07-04
I have Ubuntu 11.04 installed on a laptop.  When I run top I get a process called kworker eating 50% plus CPU.  Mouse gets sluggish and USB transfer rates gets unusable.

I tracked the bug down to the following bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281)

I found my own temporary fix by installing kernel 2.6.34-02063403-generic from kernel.ubuntu* which seems to be one of the last kernels before the kslowd/kworker thing showed up in the kernels - problem is kernel 2.6.34 is a couple of generations old and udev etc is complaining some times...I need the correct kernel.

One of the solutions proposed in the above bugs.launchpad.net post is to install the tip version of the kernel:
- tip version of kernel (git://git.kernel.org/pub/scm/linux/kernel/git/tip/linux-2.6-tip.git, from [http://lkml.org/lkml/2010/7/8/75](http://lkml.org/lkml/2010/7/8/75))


Couple of questions:  What is a tip kernel?  How do I find and install the correct one? The above link to kernel.org seems broken. My skills are towards the beginner level and would appreciate a few pointers.


Thanks!

---

### Post by ndxtg on 2011-08-11
This bug appears in kernel 2.6.35 onward (so far it's still there in 2.6.38 ), see bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779753"))

**2-step Solution: **

[LIST=1]
[*]Update kernel to 2.6.38 by installing linux image [_here_]("http://packages.ubuntu.com/source/natty/linux") (note: this kernel is for 11.04 but it is no different to 10.10 so can be use on both 10.10 and 11.04 without hassle)

[*]Then type this command in the terminal to instantly stop the lag. (thanks to [_this website_]("http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/"))
```
sudo echo N> /sys/module/drm_kms_helper/parameters/poll
```

Unfortunately on reboot, that command is no longer effective. To make it permanent, type this command and all fixed.
```
sudo echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf
```
[/LIST]


Edited: note that 2.6.38 right now does not support virtual box properly. 
Use 2.6.37 which was made by Ubuntu and for Ubuntu 10.10 [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/") instead. After updated to 2.6.37, follow step 2 above.

---

