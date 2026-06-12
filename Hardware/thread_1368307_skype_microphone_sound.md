---
title: "skype microphone sound"
date: 2009-12-30
forum: Hardware
---

### Post by sam1948 on 2009-12-30
I believe it'll work for most of u

don't install from repository
download from skype site
[http://www.skype.com/intl/en/download/skype/linux/choose/]("http://www.skype.com/intl/en/download/skype/linux/choose/")
I used the 8.10 32bit version which worked perfect

if u tried it please post u'r result
----------------------------------------------------------
the following is not must to be read.

I know there are many posts for this topic but I think this is the best solution.

my configuration is Ubuntu 9.10 Gigabyte motherboard G3M-ES2L
on-board sound device
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```
use ```
lspci | grep Audio
```
to figure out which is u'rs

---

