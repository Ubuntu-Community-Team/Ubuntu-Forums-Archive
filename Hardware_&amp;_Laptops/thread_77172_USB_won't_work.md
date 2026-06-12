---
title: "USB won't work"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by phi1 on 2005-10-16
I have a K8N Neo mainboard w/ nforce 3 chipset.

I can't get any usb device to work. I've never gotten usb to work on this hardware, but this is my first concerted attempt.



Here is the output of lsusb, no matter what's plugged in:
[FONT="Courier New"]Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/FONT]

If I plug a device in, or move one from one usb port to the next, there is a significant (4-5 sec) delay in producing the above output; otherwise, the command works instantly. The light on my Lexar JumpDrive doesn't light up; My camera says "initiallizing usb connection", but never gets further than that.




Here is the interesting part from lspci -v:

[FONT="Courier New"]0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at e3002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at e3003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
[/FONT]




Here is lsmod |grep usb; note that ehci_hcd didn't load on startup, I modprobed it. I'd like USB 2.0 high speed, but would settle for any USB for now.

[FONT="Courier New"]usbcore               104188  3 ehci_hcd,ohci_hcd[/FONT]




/var/log/messages is very long,filled with the same garbage over and over.

[FONT="Courier New"]root@ubuntu:/var/log# tail /var/log/messages
Oct 16 12:09:06 localhost kernel: [4423006.042000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:06 localhost kernel: [4423006.542000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:07 localhost kernel: [4423007.042000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:07 localhost kernel: [4423007.542000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:08 localhost kernel: [4423008.042000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:08 localhost kernel: [4423008.542000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:09 localhost kernel: [4423009.042000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:09 localhost kernel: [4423009.542000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:10 localhost kernel: [4423010.042000] ohci_hcd 0000:00:02.0: wakeup
Oct 16 12:09:10 localhost kernel: [4423010.542000] ohci_hcd 0000:00:02.0: wakeup
[/FONT]

---

### Post by phi1 on 2005-10-19
I've removed ohci_hcd (modprobe -r ohci_hcd) to stop the pointless error message spewing. 
Now, lsusb produces no output. ehci_hcd has no effect.


Does anyone know what the "wakeup" message in my post above might mean?

---

