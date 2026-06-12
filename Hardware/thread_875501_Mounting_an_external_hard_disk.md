---
title: "Mounting an external hard disk"
date: 2008-07-30
forum: Hardware
---

### Post by Stoneface on 2008-07-30
I plugged in my WD 500 Gb HDD using Ubuntu for the first time into my Ubuntu system. It isn't mounted unfortunately. Dmesg gives me these errors:
```
[   95.586189] usbcore: registered new interface driver usbhid
[   95.586436] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  103.573555] usb 1-4: new high speed USB device using ehci_hcd and address 3
[  109.920843] usb 1-4: device descriptor read/64, error -110
[  126.473689] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  142.101409] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  149.011421] usb 1-4: device descriptor read/64, error -110
[  155.423346] usb 1-4: device descriptor read/64, error -110
[  155.514154] usb 1-4: new high speed USB device using ehci_hcd and address 6
[  167.823936] usb 1-4: new high speed USB device using ehci_hcd and address 7
[  174.533313] usb 1-4: device descriptor read/64, error -110
[  194.034193] usb 1-4: new high speed USB device using ehci_hcd and address 8
[  200.370394] usb 1-4: device descriptor read/64, error -110
[  219.174465] usb 1-4: new high speed USB device using ehci_hcd and address 9
[  225.511425] usb 1-4: device descriptor read/64, error -110
[  243.700267] usb 1-4: new high speed USB device using ehci_hcd and address 10
[  250.401976] usb 1-4: device descriptor read/64, error -110
[  256.824215] usb 1-4: device descriptor read/64, error -110
[  256.915022] usb 1-4: new high speed USB device using ehci_hcd and address 11
[  269.247037] usb 1-4: new high speed USB device using ehci_hcd and address 12
[  275.627453] usb 1-4: device descriptor read/64, error -110
[  281.996984] usb 1-4: device descriptor read/64, error -110
[  282.087780] usb 1-4: new high speed USB device using ehci_hcd and address 13
[  294.466086] usb 1-4: new high speed USB device using ehci_hcd and address 14
[  300.820750] usb 1-4: device descriptor read/64, error -110
[  307.190927] usb 1-4: device descriptor read/64, error -110
[  307.311633] usb 1-4: new high speed USB device using ehci_hcd and address 15
[  319.643325] usb 1-4: new high speed USB device using ehci_hcd and address 16
[  326.029195] usb 1-4: device descriptor read/64, error -110
[  332.394977] usb 1-4: device descriptor read/64, error -110
[  332.518505] usb 1-4: new high speed USB device using ehci_hcd and address 17
[  344.413541] usb 1-4: new high speed USB device using ehci_hcd and address 18
[  350.770883] usb 1-4: device descriptor read/64, error -110
[  367.959369] usb 1-4: new high speed USB device using ehci_hcd and address 19
[  374.649192] usb 1-4: device descriptor read/64, error -110
[  381.046879] usb 1-4: device descriptor read/64, error -110
[  381.139383] usb 1-4: new high speed USB device using ehci_hcd and address 20
[  393.068822] usb 1-4: new high speed USB device using ehci_hcd and address 21
[  399.422796] usb 1-4: device descriptor read/64, error -110
[  417.891770] usb 1-4: new high speed USB device using ehci_hcd and address 22
[  424.201446] usb 1-4: device descriptor read/64, error -110
[  441.360029] usb 1-4: new high speed USB device using ehci_hcd and address 23
[  447.760169] usb 1-4: device descriptor read/64, error -110
[  454.158592] usb 1-4: device descriptor read/64, error -110
[  454.249392] usb 1-4: new high speed USB device using ehci_hcd and address 24
[  466.603722] usb 1-4: new high speed USB device using ehci_hcd and address 25
[  472.958360] usb 1-4: device descriptor read/64, error -110
[  479.355074] usb 1-4: device descriptor read/64, error -110
[  479.445878] usb 1-4: new high speed USB device using ehci_hcd and address 26
[  491.807061] usb 1-4: new high speed USB device using ehci_hcd and address 27
[  498.160104] usb 1-4: device descriptor read/64, error -110
[  504.507996] usb 1-4: device descriptor read/64, error -110
[  504.598789] usb 1-4: new high speed USB device using ehci_hcd and address 28
[  517.000573] usb 1-4: new high speed USB device using ehci_hcd and address 29
[  524.410696] usb 1-4: device descriptor read/64, error -110
[  530.811751] usb 1-4: device descriptor read/64, error -110
[  530.904227] usb 1-4: new high speed USB device using ehci_hcd and address 30
[  543.310378] usb 1-4: new high speed USB device using ehci_hcd and address 31
[  549.609690] usb 1-4: device descriptor read/64, error -110
[  568.092337] usb 1-4: new high speed USB device using ehci_hcd and address 32
[  574.445475] usb 1-4: device descriptor read/64, error -110
[  591.548606] usb 1-4: new high speed USB device using ehci_hcd and address 33
[  597.902597] usb 1-4: device descriptor read/64, error -110
[  605.373023] usb 1-4: device descriptor read/64, error -110
[  605.463827] usb 1-4: new high speed USB device using ehci_hcd and address 34
[  617.811801] usb 1-4: new high speed USB device using ehci_hcd and address 35
[  624.168314] usb 1-4: device descriptor read/64, error -110
[  643.019201] usb 1-1: new high speed USB device using ehci_hcd and address 36
[  649.306125] usb 1-1: device descriptor read/64, error -110
[  655.705490] usb 1-1: device descriptor read/64, error -110
[  655.797961] usb 1-1: new high speed USB device using ehci_hcd and address 37
[  668.213071] usb 1-1: new high speed USB device using ehci_hcd and address 38
[  674.498388] usb 1-1: device descriptor read/64, error -110
[  682.501805] usb 1-1: new high speed USB device using ehci_hcd and address 39
```

I haven't found a solution to this problem yes. Error -71 I found, but not an error 110. How do I mount the external HDD and how do I avoid this error in the future?

---

### Post by Stoneface on 2008-07-31
Well I found out that a 110 error is a time-out. But why I got that time-out I don't know yet. The I did the following: ```
sudo modprobe -r ehci_hcd
``` This inserted the module and now I can see my harddisk!!! \\:D/

---

### Post by sudeeraj on 2008-08-01
Wow Man You are a Life Saver,

All these days I had trouble getting Ubuntu to know my USB drive (Kingston 1GB)

The light was blinking about five seconds apart on the usb drive but, it was not mounted in Ubuntu.

I did a search and found out the way to find the error. (Not the solution)

But the solution was the the command you posted 

**sudo modprobe -r ehci_hcd**

My usb is now getting detected just after plug in it in, 

Thanks a Lot!
:KS:KS:KS:KS:KS:KS

---

