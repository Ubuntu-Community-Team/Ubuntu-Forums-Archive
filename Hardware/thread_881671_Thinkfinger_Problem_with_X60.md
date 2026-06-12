---
title: "Thinkfinger Problem with X60"
date: 2008-08-06
forum: Hardware
---

### Post by lawrencius on 2008-08-06
Hey every1,
I am having problems setting up my fingerprint authentication for my x60.
I already downloaded the newest version from thinkfinger, yet when I want to aquire my fingerprint the proper way (without using sudo I get this error)
```

lawrence@lawrence-laptop:~$ tf-tool --acquire

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing... done.
Error: Permission denied.
Could not open '/tmp/test.bir'.

```

Yet I also tried using sudo which worked to aquire and verify my finger but then at the login I couldn't use my finger.

Here is the tutorial I have been using:[http://en.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Ubuntu]("http://en.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Ubuntu")

I haven't found anything in previous threads about this and any help is appreciated.

Thanks ahead,
Nicholas

---

### Post by echo6 on 2008-08-08
You do not say which version you have installed but there is a bug with the configuration of the latest 0.3 version.

[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973)

---

