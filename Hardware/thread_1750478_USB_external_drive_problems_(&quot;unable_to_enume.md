---
title: "USB external drive problems (&quot;unable to enumerate USB device...&quot;)"
date: 2011-05-05
forum: Hardware
---

### Post by mbeeby on 2011-05-05
Just upgraded to 11.04. With it, I'm seeing the return of a problem I've seen sporadically for a couple of years: USB mounting seems inconsistent.

I spent the past day looking over this, and it seems that it's a widespread problem, with multiple reported solutions. None of them work for me.

I'm running 2.6.31-14-generic, as 2.6.38 locks up on boot -- I'm guessing due to similar problems, but not sure.

I have two external drives: 1tb and a 3tb SeaGate drives. The 1tb drive is recognized as /dev/sde, but the 3tb drive is never recognized.

dmesg output upon plugging in the 3tb drive:

```

[  263.380029] usb 2-3: new high speed USB device using ehci_hcd and address 8
[  278.500027] usb 2-3: device descriptor read/64, error -110
[  293.730026] usb 2-3: device descriptor read/64, error -110
[  293.960034] usb 2-3: new high speed USB device using ehci_hcd and address 9
[  309.080025] usb 2-3: device descriptor read/64, error -110
[  324.310054] usb 2-3: device descriptor read/64, error -110
[  324.543188] usb 2-3: new high speed USB device using ehci_hcd and address 10
[  329.570094] usb 2-3: device descriptor read/8, error -110
[  334.700166] usb 2-3: device descriptor read/8, error -110
[  334.940010] usb 2-3: new high speed USB device using ehci_hcd and address 11
[  339.960090] usb 2-3: device descriptor read/8, error -110
[  345.090155] usb 2-3: device descriptor read/8, error -110
[  345.200062] hub 2-0:1.0: unable to enumerate USB device on port 3
[  345.520031] usb 7-1: new full speed USB device using uhci_hcd and address 6
[  360.640038] usb 7-1: device descriptor read/64, error -110
[  375.878373] usb 7-1: device descriptor read/64, error -110
[  376.100104] usb 7-1: new full speed USB device using uhci_hcd and address 7
[  391.220054] usb 7-1: device descriptor read/64, error -110
[  406.450029] usb 7-1: device descriptor read/64, error -110
[  406.680054] usb 7-1: new full speed USB device using uhci_hcd and address 8
[  411.702054] usb 7-1: device descriptor read/8, error -110
[  416.831730] usb 7-1: device descriptor read/8, error -110
[  417.060045] usb 7-1: new full speed USB device using uhci_hcd and address 9
[  422.081412] usb 7-1: device descriptor read/8, error -110
[  427.211103] usb 7-1: device descriptor read/8, error -110
[  427.320039] hub 7-0:1.0: unable to enumerate USB device on port 1


```

It's not the cable, as I can interchange the cable used for the two drives, and the 1tb is still recognized fine, and the 3tb drive returns the same "unable to enumerate USB device" error.

I've tried adding kernel options "irqpoll", "acpi=force", to no effect.

I tried getting the ehci module to load before uhci module by inserting the this into /etc/modules:

```

ehci-hcd
uhci-hcd

```

And blacklisting them in /etc/modprobe.d/blacklist.conf:

```

blacklist ehci-hcd
blacklist uhci-hcd

```

To no effect.

In addition, my mouse is frozen for the first ~1 minute of booting, I think the relevant dmesg output is:

```

[  101.090013] usb 7-1: device descriptor read/64, error -110
[  116.350072] usb 7-1: device descriptor read/64, error -110
[  116.570084] usb 7-1: new full speed USB device using uhci_hcd and address 3
[  131.730043] usb 7-1: device descriptor read/64, error -110
[  146.970038] usb 7-1: device descriptor read/64, error -110
[  147.200049] usb 7-1: new full speed USB device using uhci_hcd and address 4
[  152.221970] usb 7-1: device descriptor read/8, error -110
[  157.351659] usb 7-1: device descriptor read/8, error -110
[  157.580121] usb 7-1: new full speed USB device using uhci_hcd and address 5
[  162.601342] usb 7-1: device descriptor read/8, error -110
[  167.732033] usb 7-1: device descriptor read/8, error -110
[  167.840080] hub 7-0:1.0: unable to enumerate USB device on port 1
[  168.120231] usb 8-1: new low speed USB device using uhci_hcd and address 2
[  168.293127] usb 8-1: configuration #1 chosen from 1 choice
[  168.309225] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input5
[  168.309307] generic-usb 0003:0461:4D22.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-1/input0

```

So it all seems interlinked...

Any ideas? I'm a bit of a noob at hacking around with this sort of configuration... (that said, it seems that this is an ongoing problem with linux and higher-speed USB)...

Thanks

---

### Post by mbeeby on 2011-05-10
bump

---

### Post by demiurg on 2011-07-16
I'm having the same issue with the most up to date version of Ubuntu

---

