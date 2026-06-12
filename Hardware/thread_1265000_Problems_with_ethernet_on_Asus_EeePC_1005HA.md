---
title: "Problems with ethernet on Asus EeePC 1005HA"
date: 2009-09-12
forum: Hardware
---

### Post by halloiz on 2009-09-12
I've been trying to get the wire/wireless connections workin' on my 1005HA using [this guide](http://ubuntuforums.org/showthread.php?t=1219931), but am experiencing some problems:

when i run "tar -xzvf AR813X-linux-v1.0.0.9.tar.gz" it says:
```
gzip: stdin: decompression OK, trailing garbage ignored
src/Makefile
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: src: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors
```

and then, when i run "make" after "cd src", i get:
```
Makefile:61: *** Linux kernel source not found. Stop.
```

Any ideas what my problem is, and how to fix it?

I'd really appreciate it if someone could help me through these issues.

btw. I'm running eeebuntu 3.0 Standard.

---

