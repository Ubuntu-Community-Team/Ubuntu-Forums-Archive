---
title: "Problem with fingerprint on HP Pavilion"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Supremus90 on 2007-10-30
Hello everybody, I have some troubles configuring the fingerprint on my HP

the device is recognised:
```
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. 
```

I followed this wiki [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger) but does not work

```
daniel@daniel-laptop:~$ sudo tf-tool --acquire
ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>
Initializing...USB device not found.
daniel@daniel-laptop:~$ sudo tf-tool --verify
ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>
Could not access /tmp/test.bir: No such file or directory
daniel@daniel-laptop:~$
```

any ideas?

---

### Post by Supremus90 on 2007-11-10
up

---

### Post by Whoopie on 2007-11-10
Try that one: [http://home.gna.org/aes2501/](http://home.gna.org/aes2501/)

If you have questions, join the IRC channel #aes2501 on OFTC.

---

