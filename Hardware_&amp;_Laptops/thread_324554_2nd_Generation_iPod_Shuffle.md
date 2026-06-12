---
title: "2nd Generation iPod Shuffle"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by brossatscu on 2006-12-23
I have a few different iPods and don't have any problem connecting them to my Ubuntu Edgy laptop. However, I just got a new Shuffle and for some reason, Linux fails to recognize that it's even connected. The lights on it will blink and then shut off when I connect it. In windows on the same computer, it works fine. Here is my dmesg:

> [17179828.804000] Call Trace:
[17179828.804000]  <c0246bae> class_device_del+0x9e/0x170  <c0246c88> class_device_unregister+0x8/0x10
[17179828.804000]  <d8b40ca0> __scsi_remove_device+0x30/0x80 [scsi_mod]  <d8b3e3fb> scsi_forget_host+0x4b/0x60 [scsi_mod]
[17179828.804000]  <d8b38a55> scsi_remove_host+0x55/0xe4 [scsi_mod]  <d8d96d8e> storage_disconnect+0xe/0x20 [usb_storage]
[17179828.804000]  <d88b7994> usb_unbind_interface+0x34/0x70 [usbcore]  <c0245e2b> __device_release_driver+0x5b/0xa0
[17179828.804000]  <c02460ec> device_release_driver+0x1c/0x30  <c0245657> bus_remove_device+0x77/0x90
[17179828.804000]  <c02446c5> device_del+0x35/0x70  <d88b5bc6> usb_disable_device+0x86/0xe0 [usbcore]
[17179828.804000]  <d88b1927> usb_disconnect+0x97/0xf0 [usbcore]  <d88b298a> hub_thread+0x27a/0xc80 [usbcore]
[17179828.804000]  <c0136180> autoremove_wake_function+0x0/0x50  <d88b2710> hub_thread+0x0/0xc80 [usbcore]
[17179828.804000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
[17179828.804000]  <c0101005> kernel_thread_helper+0x5/0x10 
[17179828.804000] Code: 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 7c 24 0c 89 04 24 8b 40 48 8b 38 89 e8 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 78 08 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 c6 07 f2 ff ba f4 
[17179828.804000] EIP: [<c0246907>] make_class_name+0x37/0xb0 SS:ESP 0068:d7c59e54
[17179828.804000]  <5>sda : READ CAPACITY failed.
[17179828.820000] sda : status=0, message=00, host=1, driver=00 
[17179828.820000] sda : sense not available. 
[17179828.824000] sda: Write Protect is off
[17179828.824000] sda: Mode Sense: 00 00 00 00
[17179828.824000] sda: assuming drive cache: write through
[17179828.824000] sd 1:0:0:0: Attached scsi removable disk sda
[17179828.824000] sd 1:0:0:0: Attached scsi generic sg0 type 0


And here is the relevant lspci:

> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller


Anyone else have a similar problem? I read somewhere of someone who had similar problems and it turned out to be a power issue. The USB ports in the front of his laptop outputed less power than those in the back. However, I know this iPod works in Windows from the same port so this shouldn't be an issue. Any ideas?

---

