---
title: "USB external hard drive issues"
date: 2008-07-16
forum: Hardware
---

### Post by Face1 on 2008-07-16
I have a problem with my external USB hard drive.  It is a external enclosure with a normal 3.5" HDD inside of it (SATA).  I recently got a new hard drive for it, and I was able to format it, mount it, etc, just fine.  Then all of a sudden it started acting up.  When I turn it on and plug it into my computer one of two things happens.  One: nothing..it never gets mounted and /dev/sdb1 is never available.  Two: it will work for some amount of time, and then stop working.  This amount of time ranges from a split second to few minutes.  Here is an example dmesg output from when it has worked for split second.```
jacob@lappy:~$ dmesg
[181856.263065] usb 5-4: new high speed USB device using ehci_hcd and address 41
[181856.374879] usb 5-4: device descriptor read/64, error -71
[181857.461494] usb 5-4: unable to read config index 0 descriptor/start: -71
[181857.461504] usb 5-4: chopping to 0 config(s)
[181857.462489] usb 5-4: string descriptor 0 read error: -71
[181857.463487] usb 5-4: string descriptor 0 read error: -71
[181857.464485] usb 5-4: string descriptor 0 read error: -71
[181857.464661] usb 5-4: no configuration chosen from 0 choices
[181857.464714] usb 5-4: USB disconnect, address 41
[181857.732599] usb 5-4: new high speed USB device using ehci_hcd and address 42
[181857.868972] usb 5-4: configuration #1 chosen from 1 choice
[181857.870048] scsi21 : SCSI emulation for USB Mass Storage devices
[181857.870421] usb-storage: device found at 42
[181857.870426] usb-storage: waiting for device to settle before scanning
[181862.860175] usb-storage: device scan complete
[181862.863905] scsi 21:0:0:0: Direct-Access     WDC WD50 00AAKS-75A7B0         PQ: 0 ANSI: 2
[181862.889714] sd 21:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[181862.892198] sd 21:0:0:0: [sdb] Write Protect is off
[181862.892207] sd 21:0:0:0: [sdb] Mode Sense: 38 00 00 00
[181862.892211] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[181862.913665] sd 21:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[181862.916160] sd 21:0:0:0: [sdb] Write Protect is off
[181862.916168] sd 21:0:0:0: [sdb] Mode Sense: 38 00 00 00
[181862.916172] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[181862.916180]  sdb: sdb1
[181862.925880] sd 21:0:0:0: [sdb] Attached SCSI disk
[181862.925951] sd 21:0:0:0: Attached scsi generic sg1 type 0
[181863.920156] kjournald starting.  Commit interval 5 seconds
[181863.926695] EXT3 FS on sdb1, internal journal
[181863.926704] EXT3-fs: recovery complete.
[181863.926710] EXT3-fs: mounted filesystem with ordered data mode.
[181865.838987] usb 5-4: USB disconnect, address 42
[181865.839622] Buffer I/O error on device sdb1, logical block 1545
[181865.839630] lost page write due to I/O error on sdb1
[181865.839721] Buffer I/O error on device sdb1, logical block 1552
[181865.839726] lost page write due to I/O error on sdb1
[181865.839736] Aborting journal on device sdb1.
[181865.839742] WARNING: at /build/buildd/linux-2.6.24/fs/buffer.c:1169 mark_buffer_dirty()
[181865.839749] Pid: 9315, comm: kjournald Not tainted 2.6.24-19-generic #1
[181865.839783]  [<c01b3aea>] mark_buffer_dirty+0x7a/0x90
[181865.839818]  [<f897e8e0>] journal_update_superblock+0x70/0xd0 [jbd]
[181865.839857]  [<f897c12f>] journal_commit_transaction+0x54f/0xda0 [jbd]
[181865.839930]  [<c01361d7>] lock_timer_base+0x27/0x60
[181865.839968]  [<f897f750>] kjournald+0xa0/0x200 [jbd]
[181865.840002]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[181865.840027]  [<f897f6b0>] kjournald+0x0/0x200 [jbd]
[181865.840048]  [<c0140982>] kthread+0x42/0x70
[181865.840056]  [<c0140940>] kthread+0x0/0x70
[181865.840073]  [<c0105677>] kernel_thread_helper+0x7/0x10
[181865.840100]  =======================
[181865.840113] Buffer I/O error on device sdb1, logical block 1545
[181865.840118] lost page write due to I/O error on sdb1
[181865.840138] journal commit I/O error
[181865.840199] Buffer I/O error on device sdb1, logical block 32702466
[181865.840204] lost page write due to I/O error on sdb1
[181865.840213] Buffer I/O error on device sdb1, logical block 52723714
[181865.840218] lost page write due to I/O error on sdb1
[181865.840226] Buffer I/O error on device sdb1, logical block 69632002
[181865.840230] lost page write due to I/O error on sdb1
[181865.840238] Buffer I/O error on device sdb1, logical block 1027
[181865.840243] lost page write due to I/O error on sdb1
[181865.840266] Buffer I/O error on device sdb1, logical block 88113154
[181865.840271] lost page write due to I/O error on sdb1
[181865.887724] Buffer I/O error on device sdb1, logical block 1545
[181865.887731] lost page write due to I/O error on sdb1
[181865.887951] Buffer I/O error on device sdb1, logical block 0
[181865.887956] lost page write due to I/O error on sdb1
[181866.087476] usb 5-4: new high speed USB device using ehci_hcd and address 43
[181866.145249] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[181866.145258] hub 5-0:1.0: hub_port_status failed (err = -32)
jacob@lappy:~$ 


```

Here is a much shorter dmesg output from when it didn't work at all: ```
[181684.701731] usb 5-1: new high speed USB device using ehci_hcd and address 39
[181684.836124] usb 5-1: configuration #1 chosen from 1 choice
[181684.837200] scsi20 : SCSI emulation for USB Mass Storage devices
[181684.837575] usb-storage: device found at 39
[181684.837580] usb-storage: waiting for device to settle before scanning
[181684.929743] usb 5-1: USB disconnect, address 39
[181685.203886] usb 5-1: new high speed USB device using ehci_hcd and address 40

```

Any ideas?

---

### Post by scrime on 2008-07-16
To me it looks like it may be a hardware issue, either the HDD enclosure, USB cable, USB port or HDD itself (I'd suspect the problem in that order).  Try it in another USB ports, try another USB cable, maybe connect the HDD to a SATA port in your PC and run a disk check tool, I use HDAT to check drives.  Test the device on another machine and see if you have any problems with it.  To me it looks like your USB is disconnecting for some reason. Well that's what I'd try.

---

### Post by timcredible on 2008-07-16
laptops usually don't output as much power through their usb ports as a desktop, you may need a Y cable to plug your drive in with so it can pull power off 2 usb ports.

---

