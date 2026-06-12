---
title: "Ibex crash"
date: 2008-11-23
forum: General Help
---

### Post by ywilliams12345 on 2008-11-23
I am getting crashes with Ibex.
It is very unpredictable, sometimes crashes after a few seconds.
Last night it ran for 2 hours, and I shutdown normally.
When it crashes, the keyboard and mouse are locked out.
Ctrl-Alt-Delete does nothing.
I have to do a hard reboot.
I attached dmesg and /var/log/messages.
Had to zip since they were so large (19.5K .txt limit).
Any advice appreciated.
thanks

AMD64
1.5GRAM
IDE HDD

---

### Post by SPr on 2008-11-23
Sorry, I can't help with the crashes but read [http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349) to see how to restart without hitting the power button.

---

### Post by ywilliams12345 on 2008-11-23
I just had another crash.
alt-print screen R+S+E+I+U+B
did not restart Ubuntu.
So it looks like the kernel crashed, and not just the display?

---

### Post by ywilliams12345 on 2008-11-23
I see the following Warning in /var/log/messages.
It happens every time I reboot:
Nov 23 07:00:48 Ubuntu kernel: [    0.372241] ACPI Warning (dsobject-0501): Package List length (6) larger than NumElements count (4), truncated

Could that be the reason I am getting a kernel crash?

---

### Post by ywilliams12345 on 2008-11-25
8.10 crashes after boot.
It runs for about 1 to 5 minutes before crashing.
About 50% of the reboots run without crashing.
This is frustrating as I am a newbie to Ubuntu.
Any suggestions on how to debug this?
thanks

---

### Post by ywilliams12345 on 2008-11-25
I wonder if this is due to my graphic chipset (on MOBO)
using system RAM?   Any pointers to help is appreciated.

---

### Post by ywilliams12345 on 2008-11-25
Attached is /var/log/Xorg.0.log
My interpretation of the log file is that the X server is recognizing
my VideoRAM properly.  Do you agree?

---

### Post by SPr on 2008-11-25
> **ywilliams12345 said:**
> I wonder if this is due to my graphic chipset (on MOBO)

Well, in dmesg I found
> 
** BUG: unable to handle kernel NULL pointer dereference at 00000008**
[   12.581953] IP: [<f89d51e0>] :agpgart:agp_generic_create_gatt_table+0x150/0x1f0
[   12.581962] *pde = 00000000 
**[   12.581966] Oops: 0000 [#1] SMP **
[   12.581969] Modules linked in: amd64_agp(+) soundcore button sis_agp snd_page_alloc shpchp pci_hotplug agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sata_sis sg usb_storage libusual pata_acpi pata_sis ohci1394 ata_generic ohci_hcd ehci_hcd ieee1394 sis900 mii usbcore libata scsi_mod dock thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   12.581989] 
[   12.581991] Pid: 2350, comm: modprobe Not tainted (2.6.27-7-generic #1)
[   12.581994] EIP: 0060:[<f89d51e0>] EFLAGS: 00010246 CPU: 0
[   12.582000] EIP is at agp_generic_create_gatt_table+0x150/0x1f0 [agpgart]
[   12.582002] EAX: 00000000 EBX: 000003ae ECX: 00000010 EDX: 00000002
[   12.582005] ESI: f7954580 EDI: 00000000 EBP: f7a23e74 ESP: f7a23e58
[   12.582007]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   12.582009] Process modprobe (pid: 2350, ti=f7a22000 task=f751d7f0 task.ti=f7a22000)
[   12.582011] Stack: f7a23e64 f7954700 00000007 00000010 000003ae 00000400 f7954580 f7a23e9c 
[   12.582017]        f89d31f4 f7554800 f7a23ed0 f89f48e1 f7954580 c026369d f7548800 ffffffed 
[   12.582022]        f7954580 f7a23ed0 f89d3456 c02636e0 ffffffff f7554c00 00000074 00000001 
[   12.582027] Call Trace:
[   12.582030]  [<f89d31f4>] ? agp_backend_initialize+0xc4/0x2a0 [agpgart]
[   12.582036]  [<f89f48e1>] ? fix_northbridge+0x66/0x2b6 [amd64_agp]
[   12.582041]  [<c026369d>] ? pci_get_subsys+0x5d/0x80
[   12.582047]  [<f89d3456>] ? agp_add_bridge+0x56/0x1a0 [agpgart]
[   12.582053]  [<c02636e0>] ? pci_get_device+0x20/0x30
[   12.582056]  [<c01199e2>] ? cache_k8_northbridges+0xd2/0x100
[   12.582062]  [<f89f4c33>] ? agp_amd64_probe+0x102/0x270 [amd64_agp]
[   12.582067]  [<f88da000>] ? agp_amd64_init+0x0/0xcd [amd64_agp]
[   12.582071]  [<f88da0c3>] ? agp_amd64_init+0xc3/0xcd [amd64_agp]
[   12.582075]  [<c0101120>] ? _stext+0x30/0x160
[   12.582078]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[   12.582083]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[   12.582090]  [<c015c208>] ? sys_init_module+0x88/0x1b0
[   12.582095]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
[   12.582098]  =======================
[   12.582099] Code: 31 db 90 8d 04 9d 00 00 00 00 8b 4e 24 89 c2 03 56 1c 89 0a 03 46 1c 8b 00 83 c3 01 3b 5d ec 7c e2 31 c0 e9 d9 fe ff ff 8d 76 00 <8b> 50 08 89 55 e8 8b 40 04 89 45 ec e9 17 ff ff ff 8d b4 26 00 
[   12.582123] EIP: [<f89d51e0>] agp_generic_create_gatt_table+0x150/0x1f0 [agpgart] SS:ESP 0068:f7a23e58
[   12.582131] ---[ end trace e7d4811c7e92484f ]---


I have no idea what that means or if it is causing your problem. I haven't had much luck with Google perhaps you will have more luck.

---

