---
title: "USB random behaviour with nVidia MCP51 controller"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by juanx on 2006-11-02
Hi all,


I'm pretty new to Ubuntu, but not so much to linux...

I'm having some trouble with my USB controller on my Asus z92m laptop.

On some boots, everything's normal. USB devices works fine, and I have no problem. But randomly, it just doesn't work.

Apparently, its some irq problem, since I see this output in my messages log:

```

Nov  2 10:56:17 localhost kernel: [  278.105203]        <ffffffff880b288a>{:usbcore:usb_hcd_irq+42} <ffffffff801685f7>{__do_IRQ+215}
Nov  2 10:56:17 localhost kernel: [  278.105241]        <ffffffff8011302f>{do_IRQ+47} <ffffffff80110460>{ret_from_intr+0}
Nov  2 10:56:17 localhost kernel: [  278.105257]         <EOI> <ffffffff80315af0>{thread_return+0} <ffffffff80315b42>{thread_return+82}
Nov  2 10:56:17 localhost kernel: [  278.105270]        <ffffffff8010e6e0>{default_idle+0} <ffffffff8010e718>{default_idle+56}
Nov  2 10:56:17 localhost kernel: [  278.105287]        <ffffffff8010e806>{cpu_idle+150} <ffffffff801202fe>{start_secondary+1278}
```

I've tried

```
sudo rmmod ohci_hcd
sudo modprobe ohci_hcd
```

and my syslog gives:

```
Nov  2 14:45:56 localhost kernel: [ 7325.839557] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 11 (level, low) -> IRQ 11
Nov  2 14:45:56 localhost kernel: [ 7325.840024] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Nov  2 14:46:04 localhost kernel: [ 7330.023845] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Nov  2 14:46:04 localhost kernel: [ 7330.023858] ohci_hcd: probe of 0000:00:0b.0 failed with error -16
```

I'm using noapic as a kernel parameter since otherwise y get some acpi timer syncing issue. Don't know if that could have some influence...

Any idea will be much appreciated.

Thanks,

Juan

---

