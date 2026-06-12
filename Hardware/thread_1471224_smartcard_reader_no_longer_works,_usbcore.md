---
title: "smartcard reader no longer works, usbcore"
date: 2010-05-03
forum: Hardware
---

### Post by ccaaee on 2010-05-03
Hi All

I have this usb smartcard reader (towitoko chipdrive micro) that worked well in 9.04 and stopped working in 9.10.  I thought I'd wait for 10.04 to try again and it still doesn't work. On the 10.04 machine(kernel2.6.32-21-generic), when plugging in the reader, a glance at /var/log/messages gives:

May  3 17:47:43 lkj11 kernel: [28358.729095] usb 2-1: new full speed USB device using uhci_hcd and address 4
May  3 17:47:43 lkj11 kernel: [28358.879764] usb 2-1: configuration #1 chosen from 1 choice
May  3 17:47:43 lkj11 kernel: [28358.881712] pl2303 2-1:1.0: pl2303 converter detected
May  3 17:47:43 lkj11 kernel: [28358.893773] usb 2-1: pl2303 converter now attached to ttyUSB0




On the 9.04 machine (kernel 2.6.28-18-server), upon plugging in the reader I get :

May  3 17:33:22 lkj10 kernel: [30391.810035] usb 2-8: new full speed USB device using ohci_hcd and address 2
May  3 17:33:22 lkj10 kernel: [30392.028180] usb 2-8: configuration #1 chosen from 1 choice
May  3 17:33:22 lkj10 kernel: [30392.106211] usbcore: registered new interface driver usbserial
May  3 17:33:22 lkj10 kernel: [30392.106245] USB Serial support registered for generic
May  3 17:33:22 lkj10 kernel: [30392.106287] usbcore: registered new interface driver usbserial_generic
May  3 17:33:22 lkj10 kernel: [30392.106291] usbserial: USB Serial Driver core
May  3 17:33:22 lkj10 kernel: [30392.124808] USB Serial support registered for pl2303
May  3 17:33:22 lkj10 kernel: [30392.124841] pl2303 2-8:1.0: pl2303 converter detected
May  3 17:33:22 lkj10 kernel: [30392.156201] usb 2-8: pl2303 converter now attached to ttyUSB0
May  3 17:33:22 lkj10 kernel: [30392.156234] usbcore: registered new interface driver pl2303
May  3 17:33:22 lkj10 kernel: [30392.156240] pl2303: Prolific PL2303 USB to serial adaptor driver
May  3 17:33:22 lkj10 pcscd: hotplug_libhal.c:342:HPAddDevice() Adding USB device: usb_device_67b_2303_noserial_if0
May  3 17:33:23 lkj10 pcscd: readerfactory.c:1082:RFInitializeReader() Attempting startup of Towitoko Chipdrive USB 00 00 using /usr/lib/pcsc/drivers/towitoko.bundle/Contents/Linux/libtowitoko.so.2.0.0
May  3 17:33:23 lkj10 pcscd: readerfactory.c:915:RFBindFunctions() Loading IFD Handler 2.0
May  3 17:33:24 lkj10 pcscd: readerfactory.c:267:RFAddReader() Using the pcscd polling thread

...etc...

So, on the machine running 9.04, the difference is a number of lines starting with usbcore ...  

Does anyone have any ideas on this??

Thanks

ccaaee

---

