---
title: "Asus P5-ND video freezes system mouse still moves ubuntu 14.04"
date: 2016-07-07
forum: Hardware
---

### Post by chvyzl106 on 2016-07-07
Hi there, I have a 14.04 system with all updates and video playback of any kind (except youtube full hd) will freeze the system the mouse still moves but the screen and everything on it are unresponsive. Any help with this would be appreciated.

---

### Post by Keen101 on 2016-07-11
Not sure if my problems are the same as yours, as my mouse does not work when my system freezes, but we may be suffering from the same problem. In my case it seems it is a well known bug in the intel 1915 graphics driver. No one has been able to come up with a complete fix yet. Although some have posted a workaround grub command that forces your system to use more power but does not let your system freeze up. In my case i am currently using the latest upstream intel nightly kernel which has improved my freezing problems some, but not entirely. I filed a bug report awhile back and was getting help until recently the kernel developer went silent. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1575467](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1575467)

My system is a Dell Inspiron though.

---

