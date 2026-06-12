---
title: "Problem with PCMCIA ethernet (3Com 589)"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by ser_bur on 2006-12-21
Hi guys !

I have problem with PCMCIA network card on an old Fujitsu-Siemens laptop.
Linux recognizes card, I can set up an IP, but cannot ping any hosts, and there's no lights at switch and card :(

Here are some info from logs:

 
**#cat /proc/interrupts**
           CPU0
  0:    1219105          XT-PIC  timer
  1:       5025          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  3:      24123          XT-PIC  serial
  5:     268107          XT-PIC  yenta, SiS SI7012
  7:          1          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:          2          XT-PIC  pcmcia0.0
 10:          3          XT-PIC  ohci1394, ohci_hcd:usb2, ehci_hcd:usb3
 11:      93661          XT-PIC  acpi, ohci_hcd:usb1, eth0
 12:     108002          XT-PIC  i8042
 14:      38165          XT-PIC  ide0
 15:      42275          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

**/var/log/messages:**

kernel: [17184658.460000] pccard: PCMCIA card inserted into slot 0
kernel: [17184658.460000] pcmcia: registering new device pcmcia0.0
kernel: [17184658.460000]  <c0139e82> setup_irq+0x102/0x110  <e0ded640> el3_interrupt+0x0/0x200 [3c589_cs]
kernel: [17184658.460000]  <c0139f29> request_irq+0x99/0xb0  <dfa97050> pcmcia_request_irq+0xd0/0x240 [pcmcia]
kernel: [17184658.460000]  <e0deda88> tc589_probe+0x1e8/0x520 [3c589_cs]  <c020a0e8> extract_buf+0xb8/0xf0
kernel: [17184658.460000]  <c01c8a68> idr_remove+0x108/0x170  <c01cc77c> vsnprintf+0x55c/0x640
kernel: [17184658.460000]  <c01c95e0> add_uevent_var+0x80/0xa0  <dfa9651e> pcmcia_bus_uevent+0x23e/0x260 [pcmcia]
kernel: [17184658.460000]  <c0115784> __activate_task+0x14/0x30  <c0115429> __wake_up_common+0x39/0x60
kernel: [17184658.460000]  <dfa96664> pcmcia_device_probe+0x54/0x100 [pcmcia]  <c022aaa4> driver_probe_device+0x44/0xc0
kernel: [17184658.460000]  <c02c4ee1> klist_next+0x31/0x50  <c022a334> bus_for_each_drv+0x44/0x70
kernel: [17184658.460000]  <c022ab96> device_attach+0x66/0x70  <c022ab20> __device_attach+0x0/0x10
kernel: [17184658.460000]  <c022a208> bus_add_device+0x28/0x110  <c02293e4> device_add+0xf4/0x150
kernel: [17184658.460000]  <dfa95e65> pcmcia_device_add+0x195/0x240 [pcmcia]  <dfa95fd2> pcmcia_card_add+0xa2/0xb0 [pcmcia]
kernel: [17184658.460000]  <c0119b6f> vprintk+0x25f/0x2e0  <dfa96060> ds_event+0x80/0xb0 [pcmcia]
kernel: [17184658.460000]  <dfa4c359> send_event+0x39/0x80 [pcmcia_core]  <dfa4c7d0> socket_insert+0x80/0xe0 [pcmcia_core]
kernel: [17184658.460000]  <dfa4cc51> pccardd+0x221/0x240 [pcmcia_core]  <c0115da0> default_wake_function+0x0/0x10
kernel: [17184658.460000]  <dfa4ca30> pccardd+0x0/0x240 [pcmcia_core]  <c0101005> kernel_thread_helper+0x5/0x10
kernel: [17184658.508000] eth1: 3Com 3c589, io 0x300, irq 9, hw_addr 00:60:97:8B:6D:1E
kernel: [17184658.508000]   8K FIFO split 5:3 Rx:Tx, auto xcvr

**dmesg:**

[17179596.892000] pccard: PCMCIA card inserted into slot 0
...
[17179597.792000] cs: IO port probe 0x100-0x3af: clean.
[17179597.792000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179597.796000] cs: IO port probe 0x820-0x8ff: clean.
[17179597.796000] cs: IO port probe 0xc00-0xcf7: clean.
[17179597.796000] cs: IO port probe 0xa00-0xaff: clean.
[17179597.796000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[17179597.804000] pcmcia: registering new device pcmcia0.0
[17179598.072000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179598.248000] eth1: 3Com 3c589, io 0x300, irq 4, hw_addr 00:60:97:8B:6D:1E
[17179598.248000]   8K FIFO split 5:3 Rx:Tx, auto xcvr
...
[17179600.392000] eth1: flipped to 10base2
...
[17179870.392000] eth1: coax cable problem

(last line is not so important because card does not have a coaxial connector).

Please, if someone has this experience, tell me what I should do... Nowhere in Internet I've found a solution - some people say it is working with no problem, other say it doesn't work :(

P.S. My system is Edgy, but card also doesn't work in Breezy, Dapper and old Knoppix with 2.4 kernel :(

---

### Post by jruschme on 2006-12-22
I'm not totally surprised by the 10Base2 message... this card is old enough that some versions shipped with a "combo cable" that had both 10Base2 and 10BaseT connectors. It picked the 10base2 connector when it didn't see anything on the 10baseT connector.

My gut feeling is to wonder if you have the wrong dongle. (Does it have a 100 led? I'm not sure if the dongles from the 3C574/575 are compatible.) That or a problem with the dongle itself or the connector on the card. (I've had 589's fail with both.)

One more thought... is your ethernet cable configured correctly? Could you accidentally be using a crossover cable?

---

