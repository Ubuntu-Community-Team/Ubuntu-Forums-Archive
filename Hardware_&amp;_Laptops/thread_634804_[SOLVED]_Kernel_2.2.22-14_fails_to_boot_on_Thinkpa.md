---
title: "[SOLVED] Kernel 2.2.22-14 fails to boot on Thinkpad R52"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by piyush_srivastava on 2007-12-08
Hello,

I tried upgrading from Feisty to Gutsy via the graphical network upgrade, but due to network problems, I had to stop it in between. Later, I completed the upgrade manually using apt-get dist-upgrade (which I had to so several times to resolve all package errors).

Now, I had kernel 2.2.22-14 on my system. However, this version fails to boot showing an error which looks like:
linear:dm-linear: Device lookup failed.....

This message appears repeatedly on the screen, preceeded by a number which changes with every instance. However, if I boot the older kernel 2.6.20-16 , it boots without any problems. The machine also runs smoothly with this kenel.

What could be the problem with the newer kernel version. If any more information is needed I shall be glad to provide it.

Thanks,

Piyush.

---

### Post by piyush_srivastava on 2007-12-08
Hello, 

The problem is solved. I had to remove evms. This is probably a [problem with evms.]("https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616")

Regards,
Piyush.

---

