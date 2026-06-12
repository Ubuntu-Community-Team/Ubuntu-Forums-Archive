---
title: "Cooler on 100% all the time"
date: 2008-10-31
forum: Hardware
---

### Post by fbn on 2008-10-31
Hi,

I've installed Ubuntu 8.10 on my Dell XPS m1330 laptop and installed the new kernel updates:

fbn@xps:~$ uname -a
Linux xps 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
fbn@xps:~$ 

Now to cooler is running on 100% all the time making big noise.

Anybody else having this issue? Some ideas what I could check to fix it?

Frank

---

### Post by mglukhovsky on 2008-10-31
You know, I just noticed that the fan is running consistently at what seems to be full speed on my Thinkpad T400 as well (didn't happen in Hardy). The fan is extremely quiet though, so I didn't notice until now. Still, that can't be good.

---

### Post by fbn on 2008-10-31
Ah damn ... it's really loud here. Any idea how to find out what the reason could be?

---

### Post by fbn on 2008-10-31
I've deinstalled the NVIDIA driver, rebooted and the problem was gone.

Do you have a NVIDIA card and the NVIDIA driver?

Anybody else who can confirm this?

I've created a bug report: [https://bugs.launchpad.net/ubuntu/+bug/291766](https://bugs.launchpad.net/ubuntu/+bug/291766)

---

