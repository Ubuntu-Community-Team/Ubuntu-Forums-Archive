---
title: "JMB38X SD Host Controller Acer 6920"
date: 2008-08-18
forum: Hardware
---

### Post by CJay554 on 2008-08-18
I'm having trouble with my ubuntu detecting this SD controller, any suggestions?

The "JMB38X SD Host Controller" i got from my windows vista hardware list prog.

heres my lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0a:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
0a:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
0a:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
0a:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384


the "0a:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381" should be given attention o.o'

---

### Post by triple.eh on 2008-08-23
I have an Acer 6920G and I can't even get lspci to list the JMicron devices.

Are you using the AMD64 or i386 distribution?  Kernel 2.6.24-19?

After hours of research, your message gives me hope the card reader on the 6920 will be recognizable and usable in Ubuntu!

BTW, have you had luck with the card reader by booting with a card in the reader as described in this post [here]("http://ubuntuforums.org/showthread.php?t=877878")?

---

### Post by CJay554 on 2008-08-29
yeah actually, i've had the SD card in the slot for a while trying many things including reboot but it never read..

---

### Post by uhappo on 2008-08-31
lsusb:
```

0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
0a:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
0a:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
0a:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
0a:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

```

So, does this mean that my firewire won't work?

What is this JMicron-thingy, can we expect Ubuntu will someday work with it?

---

### Post by CJay554 on 2008-09-16
bump plz

---

### Post by CJay554 on 2008-09-24
I tried following 
[http://www.linuxquestions.org/questions/ubuntu-63/how-to-mount-sd-card-on-ubuntu-536646/](http://www.linuxquestions.org/questions/ubuntu-63/how-to-mount-sd-card-on-ubuntu-536646/)

using sdricoh_cs but to no prevail... Anyone have any ideas on this?

---

### Post by rab4567 on 2008-09-27
I use a usb sd card reader to get around this bug until there is a fix. I love ubuntu.

---

### Post by triple.eh on 2008-12-14
Yup, looks like an external USB card reader for Acer 6920 owners is the only work around for now.  Since the Aspire One uses the same chipset for the card reader I hoped it would work.

---

