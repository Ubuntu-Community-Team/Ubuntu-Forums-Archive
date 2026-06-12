---
title: "Dell Latitude E6410"
date: 2010-09-10
forum: Hardware
---

### Post by bonfire89 on 2010-09-10
Hi all,

I am trying to install Ubuntu 10.04.1 Desktop on my Dell Latitudee E6410 laptop.

The lspci | grep VGA is

```
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

and the display chip/card is described as "32MB Intel HD Graphics"

Does anyone have any tips on getting the graphics set up properly? At the moment I have to use "nomodeset" as a grub boot option, I can't enable desktop effects and there is nothing listed in the System>administration>Hardware Drivers 

I need to properly set up the graphics card.

Any help will be much appreciated.

Thank You.

---

### Post by bonfire89 on 2010-09-10
laptop is now going into kernel panic on boot.

I'm currently trying to get 10.10 to run, but, can't get the live usb to boot yet.

I will get back when I have more details.

---

### Post by bonfire89 on 2010-09-10
using 10.10 works perfectly.

I wont mark this as solved because it could be misleading in the future.

But, I personally no longer need an answer to this.

But maybe someone will, so, if you know how to fix it, by all means, let the world know.

thanks anyway

---

### Post by sigpipe on 2010-09-10
There is a bug report tracking the issue with Intel graphics on the Latitude E6410 where you can find more information:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561802](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561802)

---

