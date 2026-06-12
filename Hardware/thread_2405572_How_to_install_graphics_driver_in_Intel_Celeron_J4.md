---
title: "How to install graphics driver in Intel Celeron J4105 with the ubuntu version 14.04"
date: 2018-11-07
forum: Hardware
---

### Post by st0302 on 2018-11-07
My ubuntu distribution version is ubuntu14.04, with the kernel version 3.18.0.
I tried to install this ubuntu on Intel Celeron J4105,but after install,the graphics driver didn't work.
I think the reason is that the launch date of Intel Celeron J4105 is too new, updating to ubuntu18.04 will works. But I don't want to update my kernel version
Is there any way to make it work in kernel 3.18.0?

---

### Post by TheFu on 2018-11-08
Support for 14.04 ends in about 6 months, so trying to solve an issue that is only good for that short of time should be considered.  

It doesn't appear that 3.18.x was ever supported for Ubuntu 14.04.x, if this link 
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support) is true.
It appears 3.13 and 4.4 are the currently supported kernels for 14.04.x supported releases.  v3.16 - v4.2 are not supported.

My 14.04.5 system runs 3.13.0-161-generic and is patched weekly.  It is a server, so there isn't any GPU support that I can test. Sorry.

---

