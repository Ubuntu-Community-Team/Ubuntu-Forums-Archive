---
title: "Problem in makefile...."
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2008-12-07
Hello,
  i am new to linux..i have an error in makefile...actually i want to compile the usbcore module using "make"...but i didnt get the .ko file....the compilation process of "make" is given below...

[B]sharief@sharief-desktop:~/Desktop/drivers/core$ make
make -C /lib/modules/2.6.26/build M=/home/sharief/Desktop/drivers/core modules
make[1]: Entering directory `/home/sharief/Desktop/kernelroot/linux2/linux-2.6.26'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/home/sharief/Desktop/kernelroot/linux2/linux-2.6.26'
sharief@sharief-desktop:~/Desktop/drivers/core$ [/B]

but when i compile the "helloworld" module its working ....its given below

[B]sharief@sharief-desktop:~/Desktop/a$ make
make -C /lib/modules/2.6.26/build M=/home/sharief/Desktop/a modules
make[1]: Entering directory `/home/sharief/Desktop/kernelroot/linux2/linux-2.6.26'
  CC [M]  /home/sharief/Desktop/a/a.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sharief/Desktop/a/a.mod.o
  LD [M]  /home/sharief/Desktop/a/a.ko
make[1]: Leaving directory `/home/sharief/Desktop/kernelroot/linux2/linux-2.6.26[/B]'

what is the problem in the first make file...how to clear that error....i am using Ubuntu 7.10...kernel version 2.6.26

---

### Post by shariefbe on 2008-12-07
This is my makefile:

[B]usbcore-objs := usb.o hub.o hcd.o urb.o message.o driver.o \
config.o file.o buffer.o sysfs.o endpoint.o \
devio.o notify.o generic.o quirks.o

ifeq ($(CONFIG_PCI),y)
usbcore-objs += hcd-pci.o
endif

ifeq ($(CONFIG_USB_DEVICEFS),y)
usbcore-objs += inode.o devices.o
endif

obj-$(CONFIG_USB) += usbcore.o

ifeq ($(CONFIG_USB_DEBUG),y)
EXTRA_CFLAGS += -DDEBUG
endif

all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/B]

---

### Post by shariefbe on 2008-12-07
can anyone explain what it is?

[B]CONFIG_PCI
CONFIG_USB_DEVICEFS
CONFIG_USB
CONFIG_USB_DEBUG
EXTRA_CFLAGS += -DDEBUG[/B]

Explain this please...or tell the link where it is explained clearly..i didnt find any link in the net...somebody help me

---

### Post by shariefbe on 2008-12-08
sorry....i am new to linux....if i ask any stupid thing forgive me..

whether i have to use **"obj-m := usbcore.o"**?

but i have **"obj-$(CONFIG_USB) += usbcore.o"**
is it different?if i have to put your code **"obj-m := usbcore.o"** in my makefile means where to put that in my makefile...kindly help me...Thanks for your patience reply

---

### Post by shariefbe on 2008-12-21
Can anyone tell me what is the error in this make :

[B]sharief@sharief-desktop:~/Desktop/drivers/host$ make
make -C /lib/modules/2.6.26/build M=/home/sharief/Desktop/drivers/host modules
make[1]: Entering directory `/home/sharief/Desktop/kernelroot/linux2/linux-2.6.26'
CC [M] /home/sharief/Desktop/drivers/host/pci-quirks.o
CC [M] /home/sharief/Desktop/drivers/host/ehci-hcd.o
CC [M] /home/sharief/Desktop/drivers/host/isp116x-hcd.o
CC [M] /home/sharief/Desktop/drivers/host/ohci-hcd.o
CC [M] /home/sharief/Desktop/drivers/host/uhci-hcd.o
CC [M] /home/sharief/Desktop/drivers/host/sl811-hcd.o
CC [M] /home/sharief/Desktop/drivers/host/sl811_cs.o
CC [M] /home/sharief/Desktop/drivers/host/u132-hcd.o
/home/sharief/Desktop/drivers/host/u132-hcd.c:250:30: error: ../misc/usb_u132.h: No such file or directory
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;read_roothub_info&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:432: error: implicit declaration of function &#8216;usb_ftdi_elan_read_pcimem&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;u132_hcd_monitor_work&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:503: error: implicit declaration of function &#8216;ftdi_elan_gone_away&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;edset_input&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:587: error: implicit declaration of function &#8216;usb_ftdi_elan_edset_input&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;edset_setup&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:597: error: implicit declaration of function &#8216;usb_ftdi_elan_edset_setup&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;edset_single&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:607: error: implicit declaration of function &#8216;usb_ftdi_elan_edset_single&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;edset_output&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:617: error: implicit declaration of function &#8216;usb_ftdi_elan_edset_output&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;u132_hcd_configure_input_recv&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:957: error: implicit declaration of function &#8216;usb_ftdi_elan_edset_empty&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;u132_hcd_endp_work_scheduler&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:1378: error: implicit declaration of function &#8216;usb_ftdi_elan_edset_flush&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;u132_periodic_reinit&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:1545: error: implicit declaration of function &#8216;usb_ftdi_elan_write_pcimem&#8217;
/home/sharief/Desktop/drivers/host/u132-hcd.c: In function &#8216;u132_hcd_start&#8217;:
/home/sharief/Desktop/drivers/host/u132-hcd.c:1816: error: dereferencing pointer to incomplete type
/home/sharief/Desktop/drivers/host/u132-hcd.c:1818: error: dereferencing pointer to incomplete type
make[2]: *** [/home/sharief/Desktop/drivers/host/u132-hcd.o] Error 1
make[1]: *** [_module_/home/sharief/Desktop/drivers/host] Error 2
make[1]: Leaving directory `/home/sharief/Desktop/kernelroot/linux2/linux-2.6.26'
make: *** [all] Error 2
sharief@sharief-desktop:~/Desktop/drivers/host$[/B]

---

### Post by shariefbe on 2008-12-23
I cleared all the errors...but modules is not installing....getting the below errors....

[B]sharief@sharief-desktop:~/Desktop/drivers/host$ modprobe ehci-hcd
FATAL: Module ehci_hcd not found.
sharief@sharief-desktop:~/Desktop/drivers/host$ modprobe uhci-hcd
FATAL: Module uhci_hcd not found.
sharief@sharief-desktop:~/Desktop/drivers/host$ modprobe ohci-hcd
FATAL: Module ohci_hcd not found.[/B]

can anyone help me what to do....

---

