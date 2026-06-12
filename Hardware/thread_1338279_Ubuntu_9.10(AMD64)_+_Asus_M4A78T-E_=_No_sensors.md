---
title: "Ubuntu 9.10(AMD64) + Asus M4A78T-E = No sensors"
date: 2009-11-26
forum: Hardware
---

### Post by hnnnashikama on 2009-11-26
System:
RAM: [Kingston ValueRam 2x2GB]("https://www.dustinhome.no/pd_5010168426.aspx")
GPU: [XFX Radeon HD4870 1GB]("https://www.dustinhome.no/pd_5010329249.aspx")
CPU: [AMD Athlon 2 X4 620]("https://www.dustinhome.no/pd_5010332422.aspx") 
Motherboard: [Asus M4A78T-E]("https://www.dustinhome.no/pd_5010223591.aspx") 
Power Supply: [Corsair VX550W]("http://www.dustinhome.no/pd_5010133748.aspx")
OS: Ubuntu 9.10(AMD64)

First off all I want to say that I'm new to GNU/Linux, I have played a little with it but dont expect to much from me.

I want to monitor my system temperature: Atleast my CPU and GPU
My problem is that I cant find any sensors, I know there are some because I can see them in the BIOS.

Tried installing [Computer Temperature Monitor]("http://computertemp.berlios.de/") but that cant find any sensors either.
Tested lm-sensors with [this]("http://www.bradtrupp.com/ubuntu-cpu-temperature.html") method, which is old put should work. No luck there.

Someone with a different motherboard tried some "modprobe" stuff, but I have no idea how to start that kind of troubleshooting.

Also tested to put: "GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax" inside the
"/etc/default/grub" with little luck. 

So far I have not come far.

I would apritiate every response i get.

- Hnnashik

---

### Post by hnnnashikama on 2009-11-29
Bump

---

### Post by geenee on 2009-11-29
I have been checking this, as I have the same problem. The output from sensors-detect states "no AMD K10 drivers available". I am afraid we will have to wait until the drivers are released. Previous iterations of the program worked fine.
Geenee          mobo ASUS M3N78-VM CPU AMD phenom 9500

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

### Post by hnnnashikama on 2009-12-02
$ wget [http://lists.lm-sensors.org/pipermai&#8230;attachment.bin]("http://lists.lm-sensors.org/pipermai...attachment.bin")
$ mkdir k10temp && mv attachment.bin k10temp/k10temp.c
 
Made a Makefile with following lines:
obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
 
$ **sudo** make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ **sudo** cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ **sudo** depmod &&** sudo** modprobe k10temp
 All this worked out, but....

 $ sudo sensors-detect
Still outputs:
#&#8212;-cut here&#8212;-
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#&#8212;-cut here&#8212;-
 
$ sudo sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +27.6°C  <&#8211; 27.6 degrees my ***
 
That tmp cant be right, right ?
Besides i have 4 CPU is there not 4 sensors ?
Should there not be a sensor for the GPU to? [COLOR=RoyalBlue]EDIT: Just fired up WoW on max settings and the temp went up to 31 degrees, is the gpu really that cold ?[/COLOR]

Btw, thx for input guys :)

---

