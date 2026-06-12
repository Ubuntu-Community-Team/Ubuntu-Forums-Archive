---
title: "dpkg --configure -a"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by banter25 on 2009-01-05
I'm trying to perform a security update on 8.10.  It keeps jamming up on two of them, linux-image-2.6.27-generic and libavcodec51. Now every time I open the synaptic package manager, I get the same following generated error that I get with the update manager.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I do? :confused: I appreciate any help.  I have only been on a Linux system for about 2 weeks now, and so far I am amazed at how friendly it actually is.

---

### Post by blazemore on 2009-01-05
Open a terminal
Type
```
sudo dpkg --configure -a
```

---

### Post by Titan8990 on 2009-01-05
A major reason I like Linux better than Windows is that when something goes wrong you often get descriptive and helpful error messages. You should get in the habit of looking closely at error messages.

You need to run:

```
sudo dpkg --configure -a
```

---

### Post by banter25 on 2009-01-05
Thanks alot guys, that was uber fast.  That's one thing that got me going on Linux, I heard it was a bunch of great guys (and some girls) that keep this thing going. Hopefully I will learn enough to start contributing.  One other thing, when I did that, I got the following error that I looked over to see if I knew what it was talking about, but alas, I'm too new to really know what it means.  I do know what it refers to, the linux image, just don't know how to make a backup of it.

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

---

### Post by donkyhotay on 2009-01-05
Basically it couldn't make a backup of your old kernel image. This *shouldn't* be an issue as it is most likely installing a new kernel image while keeping the old one.

---

### Post by banter25 on 2009-01-05
OK.  How do I get the update manager to dump it so it doesn't keep recurring?  I really appreciate all you guys do.:)

---

