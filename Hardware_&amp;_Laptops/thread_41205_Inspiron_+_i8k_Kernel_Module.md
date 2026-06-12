---
title: "Inspiron + i8k Kernel Module"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by Gtaylor on 2005-06-12
Greetings,

I'm trying to do the following:
> 
gtaylor@stimpy:/etc/init.d $ sudo modprobe i8k
FATAL: Error inserting i8k (/lib/modules/2.6.10-5-686/kernel/drivers/char/i8k.ko): No such device

I'm not sure why I'm getting this error message. I'm definitely running an Inspiron (5150) and the kernel module seems fine. Any ideas?

---

### Post by mohaham on 2005-06-19
same error here....
i have installed i8kutils too.

---

### Post by mohaham on 2005-06-19
just figured it out..
you have to do this..
sudo modprobe i8k force=1
[http://www.ubuntuforums.org/showthread.php?t=31147&highlight=i8k](http://www.ubuntuforums.org/showthread.php?t=31147&highlight=i8k)

---

