---
title: "USB external hard disk stops working after some time (ACER laptop)"
date: 2008-08-29
forum: Hardware
---

### Post by walling on 2008-08-29
Hi,

This is my first post on this forum.

I have a problem with an external hard disk connected to a USB 2.0 port. When I boot up Gnome mounts the hard disk. All is fine. I can access it for some time, half a day maybe. After that it is inaccessible. The mount point /media/disk is just an empty folder. Dmesg shows some error messages at that time.

The hard disk is a new SATA-II 500 GB Seagate disk mounted in a USB disk enclosure. The laptop is an ACER TravelMate 5512AWLMi with AMD Turion 64 CPU and 1 GB RAM. I use Hardy Heron 64 bit (x86-64).

I tried to Google a solution without much luck. I hope someone here can provide me some suggestions about how to solve it.

Thanks in advance,
Bjarke


Here are some detailed info:
```
$ uname -a
Linux bw-laptop2 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

$ dmseg
...
[   71.388008] NET: Registered protocol family 17
[   71.530239] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   74.328115] [fglrx] GART Table is not in FRAME_BUFFER range 
[   74.328126] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   74.328129] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
[   74.497007] [fglrx] interrupt source 20008000 successfully enabled
[   74.497012] [fglrx] enable ID = 0x00000004
[   74.497301] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   78.017189] hda-intel: Invalid position buffer, using LPIB read method instead.
[   78.120331] eth0: no IPv6 routers present
[   98.135132] kjournald starting.  Commit interval 5 seconds
[   98.136233] EXT3 FS on sdb1, internal journal
[   98.136236] EXT3-fs: recovery complete.
[   98.138351] EXT3-fs: mounted filesystem with ordered data mode.
[ 1578.287859] eth0: link down
[ 1579.032417] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1579.033104] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1579.686277] eth0: link down
[ 1580.270014] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1580.270525] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1584.013814] eth0: no IPv6 routers present
[ 1589.623790] eth0: no IPv6 routers present
[ 3205.989066] UDP: short packet: From 74.120.40.2:21497 36978/71 to 192.168.0.110:22994
[ 6741.385198] UDP: short packet: From 24.140.93.2:39882 42089/71 to 192.168.0.110:22994
[ 8249.827582] UDP: short packet: From 24.140.93.2:39882 62847/71 to 192.168.0.110:22994
[ 8293.543713] UDP: short packet: From 24.140.93.2:39882 43766/71 to 192.168.0.110:22994
**[16367.545833]** usb 3-7: reset high speed USB device using ehci_hcd and address 3
[16373.046540] usb 3-7: device descriptor read/64, error -110
[16378.585057] usb 3-7: device descriptor read/64, error -110
[16378.663461] usb 3-7: reset high speed USB device using ehci_hcd and address 3
[16384.164173] usb 3-7: device descriptor read/64, error -110
[16389.702672] usb 3-7: device descriptor read/64, error -110
[16389.781104] usb 3-7: reset high speed USB device using ehci_hcd and address 3
[16393.569286] usb 3-7: device not accepting address 3, error -110
[16393.609971] usb 3-7: reset high speed USB device using ehci_hcd and address 3
[16397.398147] usb 3-7: device not accepting address 3, error -110
[16397.398239] usb 3-7: USB disconnect, address 3
[16397.398404] sd 4:0:0:0: Device offlined - not ready after error recovery
[16397.398722] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[16397.398727] end_request: I/O error, dev sdb, sector 130074031
[16397.398741] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[16397.398744] end_request: I/O error, dev sdb, sector 123584575
[16397.398830] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3858433 offset 0
[16397.401118] Buffer I/O error on device sdb1, logical block 18977968
[16397.401123] lost page write due to I/O error on sdb1
[16397.401134] Buffer I/O error on device sdb1, logical block 19313537
[16397.401136] lost page write due to I/O error on sdb1
[16397.401140] Buffer I/O error on device sdb1, logical block 19339945
[16397.401141] lost page write due to I/O error on sdb1
[16397.401146] Buffer I/O error on device sdb1, logical block 19358119
[16397.401147] lost page write due to I/O error on sdb1
[16397.401152] Buffer I/O error on device sdb1, logical block 0
[16397.401154] lost page write due to I/O error on sdb1
[16397.401158] Buffer I/O error on device sdb1, logical block 15826947
[16397.401160] lost page write due to I/O error on sdb1
[16397.401164] Buffer I/O error on device sdb1, logical block 19339952
[16397.401166] lost page write due to I/O error on sdb1
[16397.401170] Buffer I/O error on device sdb1, logical block 19344133
[16397.401172] lost page write due to I/O error on sdb1
[16397.401175] Buffer I/O error on device sdb1, logical block 19344134
[16397.401176] lost page write due to I/O error on sdb1
[16397.401179] Buffer I/O error on device sdb1, logical block 19344135
[16397.401180] lost page write due to I/O error on sdb1
[16397.402528] Aborting journal on device sdb1.
[16397.404091] journal commit I/O error
[16397.404581] ext3_abort called.
[16397.404585] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[16397.404587] Remounting filesystem read-only
[16397.404918] journal commit I/O error
[16397.459170] usb 3-7: new high speed USB device using ehci_hcd and address 4
[16397.642529] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3858433 offset 0
[16397.662969] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3956737 offset 0
[16397.771747] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3956737 offset 0
[16397.783289] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3956737 offset 0
[16398.782447] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3956737 offset 0
[16399.131470] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3956737 offset 0
[16399.417888] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #3858433 offset 0
[16404.587929] usb 3-7: device descriptor read/64, error -110
[16410.126413] usb 3-7: device descriptor read/64, error -110
[16410.204848] usb 3-7: new high speed USB device using ehci_hcd and address 5
[16415.705568] usb 3-7: device descriptor read/64, error -110
[16421.244050] usb 3-7: device descriptor read/64, error -110
[16421.322492] usb 3-7: new high speed USB device using ehci_hcd and address 6
[16425.110675] usb 3-7: device not accepting address 6, error -110
[16425.151345] usb 3-7: new high speed USB device using ehci_hcd and address 7
[16428.939534] usb 3-7: device not accepting address 7, error -110
[17429.835363] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
```

---

### Post by walling on 2008-08-30
Anyone? Any idea what can be wrong with my system?

Bjarke

---

### Post by Ubun00btu on 2008-09-26
Same problem here....

Any luck?

---

### Post by walling on 2008-09-26
> **Ubun00btu said:**
> Same problem here....

Any luck?

No, I am sorry. However I see the problem often when I use certain applications, like Azureus bittorrent. It helped a lot to not use these applications. I successfully transferred large files from the local to the external hard disk, and it kept working.

I also suspect the problem maybe has something to do with one of the 64-bit drivers. I haven't tested that theory yet. I should try to boot a Ubuntu LiveCD 32-bit and running some applications known to crash the hard disk connection.

Bjarke

---

### Post by Ubun00btu on 2008-09-26
Mine tends to crash when I open a search on the Synaptic Manager, which is pretty frustrating as you can imagine.  Otherwise it seems to lock up whenever it wants to.  A Google search seems to indicate that other people with Hardy are having this problem too, expecially with laptops (I'm running a desktop). 

I'm particulary surprised because this is happening on a fresh Hardy install...

---

### Post by walling on 2008-09-26
> **Ubun00btu said:**
> Mine tends to crash when I open a search on the Synaptic Manager, which is pretty frustrating as you can imagine.  Otherwise it seems to lock up whenever it wants to.  A Google search seems to indicate that other people with Hardy are having this problem too, expecially with laptops (I'm running a desktop). 

I'm particulary surprised because this is happening on a fresh Hardy install...

Yeah, that must be frustrating. What if you use aptitude in a terminal?

I have an IBM laptop too with Hardy on and I have experienced no problems with it. But it is also 32-bit. On the other hand it seems ACER laptops are not very Linux friendly IMHO.

Bjarke

---

### Post by Ubun00btu on 2008-09-26
I have used apt-get for some apps and it seems to work ok so far, but I haven't had to install too many things yet.

---

### Post by orion2087 on 2008-10-19
I'm having the same problem and am awaiting some sort of fix. I'm using an older P3-style Celeron Toshiba laptop running Ubuntu 8.04 Server. The hard drive is an external USB seagate 500GB.

I just started having this problem yesterday through two reboots. I doesn't start until a day or so after reboot. I run rtorrent/wtorrent that constantly writes to that drive and have SMB and AFP shares out of it.

I've been running the server for a month or two without problems until now. I did do an apt-get or aptitude update this week, otherwise I haven't changed anything.

---

