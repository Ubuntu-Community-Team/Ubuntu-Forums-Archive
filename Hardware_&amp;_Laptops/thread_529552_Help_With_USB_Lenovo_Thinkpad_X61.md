---
title: "Help With USB Lenovo Thinkpad X61"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by skier on 2007-08-19
Hi everyone I am new to Linux.  The two USB ports on the right side of my laptop do not work.  The one USB port on the left side does.  Can anyone help me solve this?  



dmesg | grep -i usb

[    5.368000] usbcore: registered new interface driver usbfs
[    5.368000] usbcore: registered new interface driver hub
[    5.368000] usbcore: registered new device driver usb
[    5.372000] USB Universal Host Controller Interface driver v3.0
[    5.372000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.372000] usb usb1: configuration #1 chosen from 1 choice
[    5.372000] hub 1-0:1.0: USB hub found
[    5.476000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    5.476000] usb usb2: configuration #1 chosen from 1 choice
[    5.476000] hub 2-0:1.0: USB hub found
[    5.580000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    5.580000] usb usb3: configuration #1 chosen from 1 choice
[    5.580000] hub 3-0:1.0: USB hub found
[    5.684000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    5.684000] usb usb4: configuration #1 chosen from 1 choice
[    5.684000] hub 4-0:1.0: USB hub found
[    5.720000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    5.788000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 5
[    5.792000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.792000] usb usb5: configuration #1 chosen from 1 choice
[    5.792000] hub 5-0:1.0: USB hub found
[    5.896000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
[    5.900000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.900000] usb usb6: configuration #1 chosen from 1 choice
[    5.900000] hub 6-0:1.0: USB hub found
[    6.244000] usb 1-1: device not accepting address 2, error -71
[    7.040000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[    7.208000] usb 1-1: configuration #1 chosen from 1 choice
[    7.452000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[    7.628000] usb 1-2: configuration #1 chosen from 1 choice
[   19.804000] Bluetooth: HCI USB driver ver 2.9
[   19.892000] usbcore: registered new interface driver hci_usb
[  574.100000]  [<f889ef32>] usb_hcd_irq+0x22/0x60 [usbcore]
[  574.100000] [<f889ef10>] (usb_hcd_irq+0x0/0x60 [usbcore])

---

### Post by victorgreen on 2007-08-20
All my usb ports worked out of the box on a new Fiesty install. They work now after Ive upgraded my kernel to 2.6.22-8. 

It sounds to me like a hardware problem- Id call Levono about it. They replaced a defective power adapter for me in two days.

---

### Post by gubemton on 2008-01-02
it is probably not a hardware bug, as usb is flaky on mine as well and i have read other reports on the web too (yet no solution)

---

### Post by johj on 2008-01-04
Did you find a solution to this? Was it a hardware problem? I've got the exact same issue with my X61 - the two USB ports on the right side don't seem to detect any devices when I plug them in. They do seem to provide power though, but nothing from dmesg indicates any activity there.

---

### Post by mbsullivan on 2008-01-06
Hi All,

I, too, have had this problem with my x61 for some time... however, seeing as my laziness knows no bounds, I've just used the USB port on the left side of the laptop. If you must have the USB ports on the right side, however, I believe the following may solve your problem (solution found [here]("http://ubuntuforums.org/showthread.php?t=635977")):

Add "irqfixup" to the boot options for your kernel.  Assuming you're using GRUB as your bootloader, this entails editing /boot/grub/menu.lst.  

If you're as lazy as me, the whole process should be accomplished through the following commands:

```
sudo sed -i.bak -e 's/\(^# kopt=.*$\)/\1 irqfixup/g' /boot/grub/menu.lst && sudo update-grub
```

Let me know if you have any problems. Hope this helps!
Mike

P.S. - Reposted [for similar problem]("http://ubuntuforums.org/showthread.php?p=4071190").

---

