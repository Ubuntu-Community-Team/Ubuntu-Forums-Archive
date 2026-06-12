---
title: "USB keyboard (Microsoft comfort curve 2000) often not working"
date: 2011-06-02
forum: Hardware
---

### Post by Dmishin on 2011-06-02
Hello.
I am experiencing problems with "Microsoft comfort curve 2000" keyboard under Natty.
Symptoms: after booting up, keyboard is completely dead. Plugging keyboard in and out does not helps. Rebooting sometimes helps. though I need to reboot for 5-10 times until it starts to work. I don't know any stable way to reproduce this problem. Miscellaneous options in BIOS does not seem to affect this problem.

Once booted up successfully (with working kb), then it always works after re-plugging too.

The keyboard always perfectly **works** in BIOS and in GRUB, so it should not be a hardware problem. It stops working after the text "Starting up ..." appears (stops reacting on NumLock).

I also have USB mouse, and it works fine.

Here are the results of lsusb (Keyboard is not working):
```
$lsusb
Bus 003 Device 005: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 003 Device 003: ID 09da:000e A4 Tech Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Here is what dmesg says:
```

[    2.492040] usb 3-1: new low speed USB device using ohci_hcd and address 4
[    2.737082] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input4
[    2.737208] generic-usb 0003:045E:00DD.0004: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.1-1/input0
[    2.754565] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.1/input/input5
[    2.754702] generic-usb 0003:045E:00DD.0005: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.1-1/input1

```I don't see any errors.

I had the same problem previously (about a year ago), but then it disappeared. It appeared again after update to Natty.

Can you suggest any solution, or at least tell, what else to test?

---

### Post by Dmishin on 2011-06-03
Update:
I have tried to boot from the old Fedora 11 live CD, and it was working without any problem.
Seems that the problem is somewhere in the new kernel.
Is it possible to use older kernel with Ubuntu?
Maybe, it is worth trying to compile a custom kernel? What options can affect this problem?

---

### Post by kindlychung on 2011-06-04
Details
Manufacturer	Microsoft
Model	Comfort Curve Keyboard 2000
Bus	usb
Type	Keyboard
Id	045e
Info2	00dd

Information

[http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=040](http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=040)

System having this component

    A8N-E
    P4P800-E
    M7V
    M2NPV-VM
    HP Compaq nc8430 (RB554UT#ABC)
    MS-7255
    M2N
    C55 Host Bridge
    MS-6712
    MS-7345
    MS-7235
    M2V-TVM
    P5Q
    P5B-PLUS Series
    Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller

Module supporting this component

    usbhid

---

### Post by kindlychung on 2011-06-04
Details
Manufacturer	Microsoft
Model	Comfort Curve Keyboard 2000
Bus	usb
Type	Keyboard
Id	045e
Info2	00dd

Information

[http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=040](http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=040)

System having this component

    A8N-E
    P4P800-E
    M7V
    M2NPV-VM
    HP Compaq nc8430 (RB554UT#ABC)
    MS-7255
    M2N
    C55 Host Bridge
    MS-6712
    MS-7345
    MS-7235
    M2V-TVM
    P5Q
    P5B-PLUS Series
    Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller

Module supporting this component

    usbhid

---

### Post by Dmishin on 2011-07-10
Well, here is a kind of status report.
By some unknown reason (I suspect the famous [storm on Saturn]("http://en.wikinews.org/wiki/Cassini_spacecraft_captures_large_storm_on_Saturn")), the problem has gradually became hard to reproduce, and almost ceased. Now it is arising approximately once in 2 weeks. Due to this, I have stopped attempts to find a solution.

Thanks to the kindlychung's information, I have found a comparatively painless way to get the keyboard working, when the things has gone wrong. Executing the following code (reloading the usbhid module) as root does the thing:
```

modprobe -r usbhid
modprobe usbhid

```

Sometimes I need to execute this 2-3 times before the keyboard starts reacting.
Though it is just a workaround, it is at least much more convenient then rebooting whole system.

Anyways, I hope that it was just some quirk of my hardware, not a usbhid bug.

---

