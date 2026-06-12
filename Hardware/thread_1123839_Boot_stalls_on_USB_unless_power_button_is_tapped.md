---
title: "Boot stalls on USB unless power button is tapped"
date: 2009-04-12
forum: Hardware
---

### Post by doas777 on 2009-04-12
Hello all,

Please note, this post is NOT about running ubuntu off an usb drive. ubuntu is installed to hard disks.

I've had a boot problem with my HP dv9700 series laptop, since i upgraded to intrepid. 

When I boot, after I select the kernel in Grub, it starts to load, but hangs while attempting to detect/initialize the USB ports.

I can either hold control, for the entire boot process to move it along, or I can simply tap the powerbutton, and the boot will continue.

I've attached the output of the sourceforge boot_info_script30.sh, my lshw, and my dmesg (sorry bout the gz, it wouldn't let me attach it as txt).

in the dmesg, you can see the point at which the boot hangs, by watching the time, and noting the point where it jumps from 3.x seconds to 79.x seconds. I added the line '#--------------PROBLEM OCCURES HERE--------------#' to make it stand out.

This particular problem happens when the laptop is on AC power. the problem is MUCH worse when running on batteries alone, but since I'm rarely away from AC, I'll worry about the usb hang first.

<<Attachments redacted, as they contained system configuration informaiton>>

Thanks!
Franklin

---

### Post by doas777 on 2009-04-13
bump

---

### Post by itkeepsrepeating on 2009-04-13
Try this thread:

[http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)

Also, I had problems on my HP G50 with the wireless card hanging the boot and troubling the install on intrepid. I now am running Jaunty Beta, and it installed and runs very smoothly. Newer releases will address newer hardware.

---

### Post by doas777 on 2009-04-14
Interesting. I would not have guess it was my wifi card. I gave up on getting it to work a long time ago.

I'll start working on that angle to resolve the issue, and as you said, it's mere days until Jaunty. 

Thanks! I appreciate your response.
Franklin

---

### Post by doas777 on 2009-04-15
well, i have followed the instructions on the wifi thread, but alas, the hang remains (and still no wifi to boot).
here is the place in my dmesg where the issue occures:


```


[    2.706363] usb usb2: configuration #1 chosen from 1 choice
[    2.706589] hub 2-0:1.0: USB hub found
[    2.706722] hub 2-0:1.0: 2 ports detected
[    2.824066] usb 1-4: new low speed USB device using ohci_hcd and address 2
[    2.913120] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    2.913334] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    2.913623] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.913627] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.913967] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.914244] ehci_hcd 0000:00:02.1: debug port 1
[    2.914394] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.914418] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    3.013030] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.013500] usb usb3: configuration #1 chosen from 1 choice
[    3.013714] hub 3-0:1.0: USB hub found
[    3.013850] hub 3-0:1.0: 7 ports detected

***********HANGS HERE***************************************************

[   66.649035] Clocksource tsc unstable (delta = 4398045288922 ns)
[   66.751106] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   66.751302] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[   66.751583] ehci_hcd 0000:00:04.1: setting latency timer to 64
[   66.751587] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   66.751808] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   66.752077] ehci_hcd 0000:00:04.1: debug port 1
[   66.752225] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[   66.752234] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[   66.769100] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   66.776036] usb usb4: configuration #1 chosen from 1 choice
[   66.782818] hub 4-0:1.0: USB hub found
[   66.790615] hub 4-0:1.0: 2 ports detected
[   66.853055] usb 1-4: device not accepting address 2, error -62
[   66.912271] hub 1-0:1.0: unable to enumerate USB device on port 4
[   67.006091] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   67.013345] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   67.019921] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[   67.026753] forcedeth 0000:00:0a.0: setting latency timer to 64
[   67.353198] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   67.502653] usb 4-2: configuration #1 chosen from 1 choice
[   67.546358] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:2f:f
```

---

### Post by doas777 on 2009-04-24
upgrading to jaunty has mostly fixed the issue (it stalled on the 4th boot, but not again since), while I'm on AC, so i'll call this solved.

it still won't boot smoothly on battery, so I'll try to figure that out next.

have fun,
franklin

---

