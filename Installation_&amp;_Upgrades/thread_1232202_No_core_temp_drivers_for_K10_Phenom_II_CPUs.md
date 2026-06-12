---
title: "No core temp drivers for K10 Phenom II CPUs?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2009-08-05
I installed lm-sensors and tried adding the panel applet that displays CPU core temp. Configuration commands in the terminal says "no driver yet". 

Is there a way to display CPU temp in the panel (AKA task bar)?

[http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/](http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/)


Thanks

---

### Post by Rebelli0us on 2009-11-01
No drivers for Phenom II yet????

---

### Post by bruno9779 on 2009-11-30
There is a fix I have found [here]("http://http://blog.morrigan.ch/?p=9")

> Step for step (I’m not sure if this the newest k10temp version!):

$ wget [http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)
$ mkdir k10temp && mv attachment.bin k10temp/k10temp.c

Now create the Makefile with following lines:

    obj-m := k10temp.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)
    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod && modprobe k10temp

Enjoy it!

It workes fine for me.

I have yet to test it when the CPU is under heavy load, and to test the alarms, but sensors-applet is working fine, and the readings are consistent with the CPU load.

One thing only puzzles me: I get one sensor only for a 3 core?

---

### Post by Rebelli0us on 2009-12-03
Yep, my 550BE has only one temp sensor. Cores are very close together, and when one core heats up, heat transfers to the other core(s), so I think these temps are approximate.

---

### Post by Rebelli0us on 2010-04-13
Is Sensors applet updated to show CPU temp with Phenom II?

---

### Post by dbloom on 2010-04-15
i just installed a Phenom II and was wondering the same thing...

---

### Post by P . P . L . on 2010-07-20
Hi.

I have just built a AMD x6 1055T and running sensors or in Gkrellm

only shows one CPU temp, my Q6600 running hardy shows CPU and core temps, 

can this be fixed.

---

