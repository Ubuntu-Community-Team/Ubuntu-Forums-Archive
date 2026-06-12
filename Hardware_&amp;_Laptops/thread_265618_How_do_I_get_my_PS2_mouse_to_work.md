---
title: "How do I get my PS/2 mouse to work?"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by lwr on 2006-09-26
I haven't been able to get my PS/2 mouse to work with my laptop. Can someone please tell me how I can do this. Thanks.

---

### Post by tturrisi on 2006-09-26
it should have been detected and enabled right away.
open a terminal and try:

sudo dpkg-reconfigure xserver-xorg

and follow the prompts.

---

### Post by lwr on 2006-09-26
I tried doing that but I get the following message:
```
/var/lib/dpkg/info/xserver-xorg.prerm: line 35: /usr/bin/which: Permission denied
/var/lib/dpkg/info/xserver-xorg.prerm: line 158: /usr/bin/which: Permission denied

```
Thanks for your help.

---

