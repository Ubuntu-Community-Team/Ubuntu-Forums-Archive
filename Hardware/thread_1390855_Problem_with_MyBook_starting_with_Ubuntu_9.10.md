---
title: "Problem with MyBook starting with Ubuntu 9.10"
date: 2010-01-26
forum: Hardware
---

### Post by jpalko on 2010-01-26
I started getting this into my log after upgrading from jaunty to karmic.
```
Jan 26 10:49:45 server kernel: [   15.788132] ieee1394: sbp2: Logged into SBP-2 device
Jan 26 10:49:45 server kernel: [   15.802351] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jan 26 10:49:45 server kernel: [   15.928843] scsi 3:0:1:0: Enclosure         WD       My Book Device        PQ: 0 ANSI: 4
Jan 26 10:49:45 server kernel: [   15.929268] scsi 3:0:1:0: Attached scsi generic sg2 type 13
Jan 26 10:49:45 server kernel: [   15.932255] ------------[ cut here ]------------
Jan 26 10:49:45 server kernel: [   15.932284] WARNING: at /build/buildd/linux-2.6.31/fs/sysfs/dir.c:487 sysfs_add_one+0x98/0x100()
Jan 26 10:49:45 server kernel: [   15.932294] Hardware name: VT8623-8235
Jan 26 10:49:45 server kernel: [   15.932302] sysfs: cannot create duplicate filename '/bus/ieee1394/drivers/sbp2/0090a94450e8ca4b-1'
Jan 26 10:49:45 server kernel: [   15.932312] Modules linked in: sbp2 via_rhine e1000 mii floppy ohci1394 ieee1394
Jan 26 10:49:45 server kernel: [   15.932343] Pid: 267, comm: knodemgrd_0 Not tainted 2.6.31-17-generic #54-Ubuntu
Jan 26 10:49:45 server kernel: [   15.932352] Call Trace:
Jan 26 10:49:45 server kernel: [   15.932385]  [<c01450fd>] warn_slowpath_common+0x6d/0xa0
Jan 26 10:49:45 server kernel: [   15.932398]  [<c023b428>] ? sysfs_add_one+0x98/0x100
Jan 26 10:49:45 server kernel: [   15.932411]  [<c023b428>] ? sysfs_add_one+0x98/0x100
Jan 26 10:49:45 server kernel: [   15.932426]  [<c0145176>] warn_slowpath_fmt+0x26/0x30
Jan 26 10:49:45 server kernel: [   15.932439]  [<c023b428>] sysfs_add_one+0x98/0x100
Jan 26 10:49:45 server kernel: [   15.932453]  [<c023b839>] sysfs_do_create_link+0xd9/0x120
Jan 26 10:49:45 server kernel: [   15.932467]  [<c023b8b2>] sysfs_create_link+0x12/0x20
Jan 26 10:49:45 server kernel: [   15.932494]  [<c03a2d26>] driver_sysfs_add+0x26/0x70
Jan 26 10:49:45 server kernel: [   15.932509]  [<c03a3024>] device_bind_driver+0x14/0x30
Jan 26 10:49:45 server kernel: [   15.932524]  [<c03a306e>] device_attach+0x2e/0x80
Jan 26 10:49:45 server kernel: [   15.932539]  [<c03a1dfd>] bus_rescan_devices_helper+0x3d/0x70
Jan 26 10:49:45 server kernel: [   15.932554]  [<c03a2488>] bus_for_each_dev+0x48/0x70
Jan 26 10:49:45 server kernel: [   15.932568]  [<c03a24c6>] bus_rescan_devices+0x16/0x20
Jan 26 10:49:45 server kernel: [   15.932583]  [<c03a1dc0>] ? bus_rescan_devices_helper+0x0/0x70
Jan 26 10:49:45 server kernel: [   15.932685]  [<df83bd5e>] nodemgr_host_thread+0x1fe/0x2a0 [ieee1394]
Jan 26 10:49:45 server kernel: [   15.932723]  [<df83c580>] ? node_probe+0x0/0x60 [ieee1394]
Jan 26 10:49:45 server kernel: [   15.932760]  [<df83bb60>] ? nodemgr_host_thread+0x0/0x2a0 [ieee1394]
Jan 26 10:49:45 server kernel: [   15.932780]  [<c015be7c>] kthread+0x7c/0x90
Jan 26 10:49:45 server kernel: [   15.932793]  [<c015be00>] ? kthread+0x0/0x90
Jan 26 10:49:45 server kernel: [   15.932814]  [<c0104007>] kernel_thread_helper+0x7/0x10
Jan 26 10:49:45 server kernel: [   15.932824] ---[ end trace 59a7ce24510e3814 ]---
```

I was considering typing a bug report but I wasn't certain how to formulate my problem there in the right way. :)

There's also another annoyance with this Epia system that just keeps on filling my messages.```

Jan 26 10:51:44 server kernel: [  141.696111] longhaul: Failed to set requested frequency!
Jan 26 10:51:44 server kernel: [  141.696127] longhaul: Enabling "Ignore Revision ID" option.
Jan 26 10:51:44 server kernel: [  141.908106] longhaul: Failed to set requested frequency!
Jan 26 10:51:44 server kernel: [  141.908122] longhaul: Disabling ACPI C3 support.
Jan 26 10:51:44 server kernel: [  141.908129] longhaul: Disabling "Ignore Revision ID" option.
Jan 26 10:51:44 server kernel: [  142.120080] longhaul: Failed to set requested frequency!
Jan 26 10:51:44 server kernel: [  142.120095] longhaul: Enabling "Ignore Revision ID" option.
Jan 26 10:51:45 server kernel: [  142.332081] longhaul: Failed to set requested frequency!
Jan 26 10:51:59 server kernel: [  156.224082] longhaul: Failed to set requested frequency!
Jan 26 10:51:59 server kernel: [  156.544080] longhaul: Failed to set requested frequency!
```

lspci output
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:14.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)
```

For this one I think I already found a solution:
```
Jan 26 10:42:02 server kernel: [ 2616.000453] ieee1394: sbp2: aborting sbp2 command
Jan 26 10:42:02 server kernel: [ 2616.000472] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 22 95 2d 2f 00 00 20 00
Jan 26 10:43:13 server kernel: [ 2687.220734] longhaul: Warning: Timeout while waiting for idle PCI bus.
```

That got fixed by creating file /etc/modprobe.d/sbp2 that contained "options sbp2 serialize_io=1 max_speed=2". At least it no longer bothered my system. :)

I noticed however that there have been a ot of bug reports for kernel 2.6.31 that complained about "/build/buildd/linux-2.6.31/fs/sysfs/dir.c" problems. Hopefully there's a simple solution for this or a workaround for now. Does anyone know some solution?

---

