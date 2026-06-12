---
title: "FATAL: Module ehci_hcd not found"
date: 2010-07-14
forum: Hardware
---

### Post by SeePU on 2010-07-14
FATAL: Module ehci_hcd not found.

```
$ modprobe -r ehci_hcd
FATAL: Module ehci_hcd not found.
```

I can't use usb hard drives, either SATA HDDs connected via USB or USB flash drives with my Lubuntu install.  

Is this a bug?

I had the same problem in Debian Squeeze but running the above command didn't result in the 'FATAL..' message.  I eventually got it to work.

dmesg shows:
```
[  877.152370] hub 1-0:1.0: unable to enumerate USB device on port 3
[  877.340305] hub 1-0:1.0: unable to enumerate USB device on port 3
[  877.528378] hub 1-0:1.0: unable to enumerate USB device on port 3
[  877.716424] hub 1-0:1.0: unable to enumerate USB device on port 3
[  877.904362] hub 1-0:1.0: unable to enumerate USB device on port 3
[  878.148078] usb 1-3: new high speed USB device using ehci_hcd and address 60
[  878.990401] end_request: I/O error, dev fd0, sector 0
[  878.990417] Buffer I/O error on device fd0, logical block 0]
```
Any ideas?

---

### Post by cavalier911 on 2010-07-14
Support for hardware is compiled into the kernel if =y as module if =m
```
cat /boot/config-2.6.32-21-generic | grep -i ehci
```
returns 
```
CONFIG_USB_ARCH_HAS_EHCI=y
CONFIG_USB_EHCI_HCD=y
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_EHCI_TT_NEWSCHED=y

```
Support is compiled into the kernel
Grep my machines dmesg for ehci.
```
dmesg | grep -i ehci
```
Returns
```
[    0.535711] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.542832] ehci_hcd 0000:00:0e.2: PCI INT C -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.543006] ehci_hcd 0000:00:0e.2: EHCI Host Controller
[    0.543530] ehci_hcd 0000:00:0e.2: new USB bus registered, assigned bus number 1
[    0.543814] ehci_hcd 0000:00:0e.2: irq 9, io mem 0xf400a000
[    0.553809] ehci_hcd 0000:00:0e.2: USB 2.0 started, EHCI 0.95
[    0.908002] usb 1-2: new high speed USB device using ehci_hcd and address 2
mojo@lubuntu:~$ dmesg | grep -i ehci
[    0.535711] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.542832] ehci_hcd 0000:00:0e.2: PCI INT C -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.543006] ehci_hcd 0000:00:0e.2: EHCI Host Controller
[    0.543530] ehci_hcd 0000:00:0e.2: new USB bus registered, assigned bus number 1
[    0.543814] ehci_hcd 0000:00:0e.2: irq 9, io mem 0xf400a000
[    0.553809] ehci_hcd 0000:00:0e.2: USB 2.0 started, EHCI 0.95
[    0.908002] usb 1-2: new high speed USB device using ehci_hcd and address 2

```

---

### Post by SeePU on 2010-07-15
Thanks for the suggestions but it didn't work.  

I get similar output but the usb drive is not detected.  

sudo fdisk -l just shows the laptop drive.  

So, I can't use a usb drive (whether SATA connected via usb or usb thumb drive)?  

I guess that means Lubuntu is worthless then.  I figure it's a bug.  It shouldn't be this hard.  I will abandon the *buntus on my laptop... I have no choice.  If devs don't care about users who have usb drives, then I don't care about the *buntus!!!!

---

### Post by IcarusR on 2010-07-15
Never mind, didn't read OP properly

---

