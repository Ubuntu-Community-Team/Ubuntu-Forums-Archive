---
title: "[solved] Jaunty CPU scaling steps misdetected"
date: 2009-05-15
forum: Hardware
---

### Post by scorchedbysun on 2009-05-15
I had already posted about this during the development of Jaunty:

[http://ubuntuforums.org/showthread.php?t=1095081](http://ubuntuforums.org/showthread.php?t=1095081)

Since I can't post there any more and I solved the problem, I decided to post here.

The solution, in a nutshell, is to install the -386 kernel (instead of the -generic one). It includes the powernow_k7 module and works as before.

I wrote down the complete procedure here:

[http://www.ode2.com/?p=10](http://www.ode2.com/?p=10)

Additionally, this solves the problem of the system starting in "performance" mode; it always starts in "ondemand" mode now.

I'd still like to know if there is some option or parameter I can pass to the -generic kernel to make it behave correctly.

---

