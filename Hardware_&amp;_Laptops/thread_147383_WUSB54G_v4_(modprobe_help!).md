---
title: "WUSB54G v4 (modprobe help!)"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by Kube on 2006-03-20
Hello...I've just started using Ubuntu, and hence Linux, a week ago..so still quite noobish :(

Ok...I've tried installing the linksys adapter wusb54gv4 (driver=rt2500usb.inf)into breezy, and so followed the guide to install ndiswrapper in the wiki.

All goes well until I hit the "modprobe ndiswrapper" command. Reading around, I think it loops and hangs the terminal...

Here's what I got from the error log:

joelfooxj@ubuntu:~$ tail /var/log/messages
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [pg0+546558251/1069716480] register_devices+0x42b/0x648 [ndiswrapper]
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [sys_getdents64+204/226] sys_getdents64+0xcc/0xe2
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [pg0+546558987/1069716480] wrapper_ioctl+0xc3/0xcd [ndiswrapper]
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [do_ioctl+111/169] do_ioctl+0x6f/0xa9
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [vfs_ioctl+101/481] vfs_ioctl+0x65/0x1e1
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [sys_ioctl+133/146] sys_ioctl+0x85/0x92
Mar 20 16:34:28 localhost kernel: [4295135.260000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Mar 20 16:34:28 localhost kernel: [4295135.260000] Code: 0c 8b 74 24 10 89 d0 83 c4 14 c2 0c 00 83 ec 10 89 74 24 04 8b 74 24 18 89 6c 24 0c 85 f6 89 1c 24 89 7c 24 08 8b 6c 24 14 74 56 <0f> b7 16 0f b7 4d 02 8b 7d 04 66 39 ca 0f b7 c1 0f b7 da 0f 43
Mar 20 16:34:28 localhost kernel: [4295135.260000]  <3>ndiswrapper (wrapper_init:1534): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'
Mar 20 16:34:28 localhost kernel: [4295135.282000] usbcore: deregistering driver ndiswrapper


From what I can see here...apparently ndiswrapper get's uninstalled from the kernel? Because after that I try the command "ndiswrapper -l" to list my drivers, but it just hangs the terminal again. 

I have to reboot before "ndiswrapper -l" works. And when it does, it IS able to display the driver and hardware present...

Thanks.

---

