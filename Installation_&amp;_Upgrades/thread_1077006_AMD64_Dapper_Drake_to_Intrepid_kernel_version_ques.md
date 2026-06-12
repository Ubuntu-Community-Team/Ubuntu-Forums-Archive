---
title: "AMD64 Dapper Drake to Intrepid kernel version question"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by rdilliker on 2009-02-21
I upgraded my AMD64 based machine from Dapper Drake to 8.04 and then 8.10 and I have a few questions about the kernel version that I now have installed. When I run uname -a I get:
```
Linux Athlon 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

```

I found on another thread that "generic" just means the kernel is generic to all 64-bit x86 processors. As I recall it when I was running Dapper Drake the kernel version specifically had amd64 at the end of it. So just to confirm, am I really running the 64-bit kernel? I am just wondering why this is. Is there some place I can go to check what the latest kernel version is for each release of Ubuntu? 

The other odd thing is that my GRUB menu contains another installed kernel that shows up like this: ```
Ubuntu 8.10, kernel 2.6.15-53-amd64-generic
```
This makes me think that indeed the "generic" kernel is not the 64-bit one. The problem is when I try to start this 2.6.15-53-amd64-generic kernel I get a whole bunch of errors involving my nvidia graphics card as well as failures mounting local filesystems and other errors.

Any help is greatly appreciated!

---

### Post by rdilliker on 2009-02-22
Bump.

---

