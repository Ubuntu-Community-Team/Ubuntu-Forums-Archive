---
title: "USR hardware modem crashes PPC kernel"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by xeex on 2005-04-09
I have a 3Com/USR hardware modem, model 0778, 3CP5610A. According to any list I can find, it's not a winmodem and should work just fine in Linux. My computer is an Apple G4/400 Gigabit Ethernet. (The modem works in OS X, BTW.)

However, I get a kernel panic on every boot. I tried all the PCI slots, and the same thing happens. I also removed the one other PCI card I'm using (which works fine). This is the text I see before reboot:

```
Oops: kernel access of bad area, sig: 11[#1]
NIP: C0117B38 LR: C011AEC4 SP: C03D3D80 REGS: c03d3cd0 TRAP: 0300    Not tainted
MSR: 00009032 EE: 1 PR: 0 FP: 0 ME: 1 IR/DR: 11
DAR: 00000014, DSISR: 40000000
TASK = c03d1670[1] 'swapper' THREAD: c03d2000
Last syscall: 120
GPR00: 00000000 C03D3D80 C03D1670 C0249878 C02FA008 00000000 00000000 00000000
GPR08: 00000008 00000000 C02FA008 00000000 00000000 00000000 00000000 00000000
GPR16: 00000000 00000000 00000000 00000000 00000000 00220000 C1D42448 11000040
GPR24: 00000001 C1C57660 C0259D94 C03D3DF0 C0259878 00000000 C02FA008 C02FA008
NIP [c0117b38] uart_remove_one_port+0x38/0xdc
LR [c011aec4] serial8250_register_port+0x6c/0x128
Call trace:
 [c011aec4] serial8250_register_port+0x6c/0x128
 [c011be6c] pciserial_init_one+0x170/0x28c
 [c00bb634] pci_device_probe_static+0x6c/0x88
 [c00bb6a0] __pci_device_probe+0x50/0x70
 [c00bbff0] pci_device_probe+0x30/0x60
 [c0120608] driver_probe_device+0x4c/0xa0
 [c01207c4] driver_attach+0x88/0xc8
 [c0120db0] bus_add_driver+0xa0/0x10c
 [c012143c] driver_register+0x30/0x40
 [c00bba18] pci_register_driver+0x70/0xa0
 [c02a7da0] serial8250_pci_init+0x18/0x28
 [c02846f0] do_initcalls+0x54/0xfc
 [c0004000] init+0x2c/0xf4
 [c0006bf4] kernel_thread+0x44/0x60
Kernel panic - not syncing: Attempted to kill init!
 <0>Rebooting in 180 seconds..
```

Any advice on how to fix this? I'm out of luck without a modem, and out of cash to buy another.

Thanks!

---

