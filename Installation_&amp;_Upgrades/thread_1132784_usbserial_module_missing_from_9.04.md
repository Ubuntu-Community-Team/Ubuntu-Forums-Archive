---
title: "usbserial module missing from 9.04?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2009-04-22
I upgraded to 9.04 the other day, and I see that the usbserial module is not available in the kernel that ships with 9.04, 2.6.28-11-generic. It is there in the 8.10 kernels:

```
$ ls /lib/modules/ | more
2.6.27-11-generic
2.6.27-7-generic
2.6.28-11-generic
$ find /lib/modules/ -name usbserial*
/lib/modules/2.6.27-7-generic/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/usb/serial/usbserial.ko

```

why is it missing?

---

### Post by zekica on 2009-04-22
It is compiled into kernel. If you open: **/usr/src/linux-headers-2.6.28-11-generic/.config**, it will contain: **CONFIG_USB_SERIAL=y**

---

### Post by akos.maroy on 2009-04-22
> **zekica said:**
> It is compiled into kernel. If you open: **/usr/src/linux-headers-2.6.28-11-generic/.config**, it will contain: **CONFIG_USB_SERIAL=y**

indeed.

but then, how do I get usbserial the handle a device that it normally doesn't? if it's compiled as a module, I can issue:

```
modprobe usbserial vendor=0xffff product=0x0005
```

but this way, I can't :(

---

### Post by weijoewang on 2009-04-24
Yes, I also have this question..

I don't know how to manually probe a usbserial device since the module is not a visible "module" any more..:(

---

### Post by fabiobh0 on 2009-04-30
There is a bug for this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002")

usbserial has been moved back into a module. It should appear in the next kernel builds.

---

### Post by akos.maroy on 2009-05-01
> **fabiobh0 said:**
> There is a bug for this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002")

usbserial has been moved back into a module. It should appear in the next kernel builds.

good news - waiting for the kernel update...

---

### Post by loonsailor on 2009-05-02
This is killing me as well.  I don't see how to load the new "proposed" kernel.  I followed the instructions, but I'm not sure what module to tell aptitude to load.  FWIW, I usually use synaptic.  Is there a way to load the new proposed kernel with that?

Thanks

---

