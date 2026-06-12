---
title: "RF keyboard suddenly dies"
date: 2010-03-16
forum: Hardware
---

### Post by linuxgrrl on 2010-03-16
Hello, 
I have an Adesso RF mini keyboard / trackball combo that I'm using with a home theater pc. It works fine 95+ percent of the time, but every couple weeks or so, the receiver suddenly becomes completely non-responsive.  As in, the light on the USB receiver dongle does not flash and no inputs are accepted.  This is a showstopper problem on the WAF front ... if the HTPC is not reliable, I will be forced to dismantle it and move it to the garage.:-(  Unplugging the dongle and moving it to another USB port usually solves the problem, but no one else but me will be willing to fuss with this.

A moment ago, the freeze happened while I was in the act of typing so I'm taking the opportunity to write.  My dmesg and syslog files are shown below; but they also reflect me unplugging/replugging the dongle so I'm not sure if there's actually any useful information in them.  The GL faults could have happend yesteray, I'm just including them for context.
Help!!!!

From syslog:
```
Mar 16 20:13:42 mythbox avahi-daemon[1143]: last message repeated 5 times
Mar 16 20:17:01 mythbox CRON[20029]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 16 20:30:18 mythbox kernel: [386751.644764] usb 2-3: USB disconnect, address 2
Mar 16 20:30:18 mythbox kernel: [386751.644773] usb 2-3.1: USB disconnect, address 4
Mar 16 20:30:25 mythbox kernel: [386758.211316] usb 1-6: new high speed USB device using ehci_hcd and address 3
Mar 16 20:30:25 mythbox kernel: [386758.363653] usb 1-6: configuration #1 chosen from 1 choice
Mar 16 20:30:25 mythbox kernel: [386758.363879] hub 1-6:1.0: USB hub found
Mar 16 20:30:25 mythbox kernel: [386758.363990] hub 1-6:1.0: 4 ports detected
Mar 16 20:30:25 mythbox kernel: [386758.643237] usb 1-6.1: new low speed USB device using ehci_hcd and address 4
Mar 16 20:30:25 mythbox kernel: [386758.765769] usb 1-6.1: configuration #1 chosen from 1 choice
Mar 16 20:30:25 mythbox kernel: [386758.775074] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6.1/1-6.1:1.0/input/input7
Mar 16 20:30:25 mythbox kernel: [386758.775230] generic-usb 0003:1241:F767.0004::
```

From dmesg:
```
[128176.611221] npviewer.bin[8536]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ff90a77c error 14
[188437.997836] compiz.real[2535]: segfault at 10 ip 00007fde7efd3f07 sp 00007fffda7780b8 error 4 in libGLcore.so.185.18.36[7fde7e4dd000+dda000]
[296073.930038] CE: hpet2 increasing min_delta_ns to 15000 nsec
[380764.897860] npviewer.bin[16445]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ff8dd3fc error 14
[386751.644764] usb 2-3: USB disconnect, address 2
[386751.644773] usb 2-3.1: USB disconnect, address 4
[386758.211316] usb 1-6: new high speed USB device using ehci_hcd and address 3
[386758.363653] usb 1-6: configuration #1 chosen from 1 choice
[386758.363879] hub 1-6:1.0: USB hub found
[386758.363990] hub 1-6:1.0: 4 ports detected
[386758.643237] usb 1-6.1: new low speed USB device using ehci_hcd and address 4
[386758.765769] usb 1-6.1: configuration #1 chosen from 1 choice
[386758.775074] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6.1/1-6.1:1.0/input/input7
[386758.775230] generic-usb 0003:1241:F767.0004: input,hidraw1: USB HID v1.10 Keyboard [HOLTEK Wireless 2.4GHz Trackball Keyboard] on usb-0000:00:12.2-6.1/input0
[386758.785043] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6.1/1-6.1:1.1/input/input8
[386758.785304] generic-usb 0003:1241:F767.0005: input,hiddev97,hidraw2: USB HID v1.10 Mouse [HOLTEK Wireless 2.4GHz Trackball Keyboard] on usb-0000:00:12.2-6.1/input1
```

---

