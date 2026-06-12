---
title: "Enabling USBFS in ubuntu 10.04"
date: 2010-07-16
forum: Hardware
---

### Post by kishon on 2010-07-16
I need to enable usbfs in 10.04. I heard it's enabled in 9.10 but  removed in 10.04. is there any way by which I can enable usbfs in 10.04  as i don't want to downgrade my ubuntu to 9.10.

Thanks.

---

### Post by anglican on 2010-07-16
> **kishon said:**
> I need to enable usbfs in 10.04. I heard it's enabled in 9.10 but  removed in 10.04. is there any way by which I can enable usbfs in 10.04  as i don't want to downgrade my ubuntu to 9.10.

Thanks.
There may be a workaround that you can use, take a look at:

[http://ubuntuforums.org/showthread.php?t=1493771](http://ubuntuforums.org/showthread.php?t=1493771)

Otherwise you could try compiling your own kernel with usbfs enabled, but be warned: it wasn't disabled for no reason. There may be clashes with other things. If you want to have a go at compiling a kernel, a reasonable starting place is:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

H

---

