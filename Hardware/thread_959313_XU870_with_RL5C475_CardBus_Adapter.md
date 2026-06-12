---
title: "XU870 with RL5C475 CardBus Adapter"
date: 2008-10-26
forum: Hardware
---

### Post by milmber on 2008-10-26
Hi,
I am trying to use a Merlin XU870 with a Ricoh RL5C475 cardbus adapter under Ubuntu 8.04 (kernel 2.6.24-21-server). The kernel "sees" the Ricoh RL5C475, but once I insert the Novotel Merlin XU870, it is not bound to /dev/ttyUSB0,etc...

From dmesg after startup without the XU870 inserted...

```
[   48.218904] Yenta: CardBus bridge found at 0000:01:05.0 [0000:0000]
[   48.359123] Yenta: ISA IRQ mask 0x0000, PCI irq 16
[   48.359129] Socket status: 30000006
[   48.359132] Yenta: Raising subordinate bus# of parent bus (#01) from #02 to #05
[   48.359140] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xafff
[   48.359145] cs: IO port probe 0x8000-0xafff: clean.
[   48.360482] pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfaffffff
```

lspci shows the cardbus adapter as being detected:

```

~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
01:04.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
**01:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)**
01:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
```

On insertion of the XU870 the following appears:

```
[  453.264214] pccard: CardBus card inserted into slot 0
[  453.377589] irq 16: nobody cared (try booting with the "irqpoll" option)
[  453.377664] Pid: 0, comm: swapper Not tainted 2.6.24-21-server #1
[  453.377696]  [<c016e304>] __report_bad_irq+0x24/0x80
[  453.377721]  [<c016e5db>] note_interrupt+0x27b/0x2c0
[  453.377746]  [<c016d800>] handle_IRQ_event+0x30/0x60
[  453.377762]  [<c016efa6>] handle_fasteoi_irq+0x86/0xe0
[  453.377778]  [<c010a92b>] do_IRQ+0x3b/0x70
[  453.377803]  [<c0108def>] common_interrupt+0x23/0x28
[  453.377840]  [<c01062e6>] mwait_idle_with_hints+0x46/0x60
[  453.377860]  [<c01066c3>] cpu_idle+0x73/0xd0
[  453.377874]  [<c043ca8f>] start_kernel+0x31f/0x3b0
[  453.377882]  [<c043c150>] unknown_bootoption+0x0/0x1f0
[  453.377914]  =======================
[  453.377916] handlers:
[  453.377963] [<f8a78880>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[  453.378087] Disabling IRQ #16
```

It seems though something is wrong from the output above?

The "pccard status" command provides the following to confirm that the card insertion was detected:

```
~$ pccard status
Socket 0:
  3.3V 32-bit PC Card

```


"pccard info" and "pccard ident" come up empty though?
```

~$ pccardctl ident
Socket 0:
  no product info available
~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```

Loading the "airprime" module gives the following:

```
[  481.536257] usbcore: registered new interface driver usbserial
[  481.536284] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  481.536305] usbcore: registered new interface driver usbserial_generic
[  481.536308] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  481.540771] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[  481.540805] usbcore: registered new interface driver airprime
```

Anyone have any ideas as to how to get the card working? It works fine in Windows and on MacOSX (so it's not the XU870 card). I've read some posts that I should not use pcmcia-cs, but instead the kernel pcmcia modules. Other posts point to editing my /etc/pcmcia/config.opts file, but this is supposed to have been superseded by the hotplug system?
Any help would be greatly appreciated.

---

