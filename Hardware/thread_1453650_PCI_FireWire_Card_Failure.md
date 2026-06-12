---
title: "PCI FireWire Card Failure"
date: 2010-04-13
forum: Hardware
---

### Post by WSkelton on 2010-04-13
I cant seem to get my firewire card to function in 9.10.

lspci returns:
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)

grep 1394 /var/log/kern.log returns:
Apr 13 10:22:25 Server kernel: [    2.151097] ohci1394 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 13 10:22:25 Server kernel: [    2.208013] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
Apr 13 10:22:25 Server kernel: [    2.304050] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 13 10:22:25 Server kernel: [    2.308008] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
Apr 13 10:22:25 Server kernel: [    3.416010] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
Apr 13 13:56:10 Server kernel: [    2.138344] ohci1394 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 13 13:56:10 Server kernel: [    2.196016] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
Apr 13 13:56:10 Server kernel: [    2.293561] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 13 13:56:10 Server kernel: [    2.297529] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
Apr 13 13:56:10 Server kernel: [    3.412012] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]

Not sure what to do next.

---

