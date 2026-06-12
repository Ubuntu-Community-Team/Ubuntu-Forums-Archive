---
title: "XUBUNTU on a Sony Vaio PCG-F180 (old laptop)"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Awl77 on 2008-01-24
I just installed XUBUNTU 7.10 on my old laptop and got it running great. I had a terrible time getting it to boot initially from the live CD. It was shutting down just after  the CD Install menu no matter which type of boot I chose . I tried tons of stuff (apci=off/force...) and was about to give up when I found the following page: 

[http://www.physik.uni-freiburg.de/~zwerger/cip/Vaio/software-fix_Linux.htm]("http://www.physik.uni-freiburg.de/~zwerger/cip/Vaio/software-fix_Linux.htm")

The key to getting it going was adding ***apm=off no-hlt*** to the GRUB boot. Once I figured that out xubuntu installed fine. Apci is not running and I get a warning about it when I boot but I'm not sure if its a big deal. It also won't shut down completely on its own. (stops at the xubunu "unloading" screen) Other then that everything is working great. Still need to test things out but am very happy that I didn't have to put windows 98 back on it.

Maybe this info can help out other old vaio users withe same issue.

---

### Post by ronalddevos on 2008-03-08
It certainly did help: after ploughing through the 'Net for a day or so I found many problems, no working solutions - this did it.
It still does not recognise the native PCMCIA CD Drive, but after hooking up an old USB CD drive it automatically installed on my VAIO Z600TEK from this second drive.
Another step away from Windows!

---

### Post by kerry_s on 2008-03-08
debian works better on the old rigs. i'm using a debian custom install on a vaio pcg-f430 works perfectly. stay with the 2.6.18 kernel though, the 2.6.23 sucks.

---

