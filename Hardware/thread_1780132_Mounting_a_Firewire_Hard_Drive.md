---
title: "Mounting a Firewire Hard Drive"
date: 2011-06-11
forum: Hardware
---

### Post by muzicman82 on 2011-06-11
Hello,

I just installed a new clean copy of 11.04 onto a Dell XPS M1710 laptop. I believe it has a generic Texas Instruments Firewire controller. 

Plugging in a standard Firewire disk does nothing. 

If I boot with the device and run &#8220;dmesg|grep firewire&#8221;, I get:
```
[    1.327138] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.388103] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.888144] firewire_core: created device fw0: GUID 354fc0001a369961, S400
[    1.888154] firewire_core: giving up on config rom for node id ffc1
[    1.888158] firewire_core: giving up on config rom for node id ffc2

```
sudo fdisk -lu returns:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068e98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   481583103   240790528   83  Linux
/dev/sda2       481585150   488396799     3405825    5  Extended
/dev/sda5       481585152   488396799     3405824   82  Linux swap / Solaris
```

The listed drive and partitions are the internal drive and not the external.

How can I install the necessary modules to make this work?

---

### Post by d.donald on 2011-07-03
Hello muzicman82,

I have got the same problem but with an upgraded installation of 11.04

In the kern.log when I connect my external firewire hard drive:
Jul  3 15:02:47 firebird kernel: [16413.987732] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jul  3 15:02:47 firebird kernel: [16413.987786] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jul  3 15:02:47 firebird kernel: [16413.987837] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jul  3 15:02:47 firebird kernel: [16413.987885] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jul  3 15:02:47 firebird kernel: [16413.987933] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jul  3 15:03:18 firebird kernel: [16444.560037] firewire_core: giving up on config rom for node id ffc0

Nothing appears in my hard drives

It seems the rights modules are here:

lsmod | grep -i firewire
firewire_sbp2          18303  0 
firewire_ohci          31504  0 
firewire_core          56138  2 firewire_sbp2,firewire_ohci
crc_itu_t              12627  1 firewire_core

Have you solved your problem ?

---

