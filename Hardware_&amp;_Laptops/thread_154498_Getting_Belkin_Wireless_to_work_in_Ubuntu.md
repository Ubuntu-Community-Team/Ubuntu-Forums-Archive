---
title: "Getting Belkin Wireless to work in Ubuntu"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by djmdave on 2006-04-03
Greetings chaps! :)

I've been using ubuntu for 2 days now, and having never used any Linux distro before, I'm obviously having problems!

I want to get my Belkin F5D7050 Wifi USB adapter to work with ubuntu, and I've been using ndiswrapper to try and sort it out. I've been following the installation wiki and I've got up to the part where you use modprobe using this command:

```
sudo modprobe ndiswrapper
```

After entering that I don't get any feedback from ndiswrapper at all, and any ndiswrapper commands after that not work untill I reboot.

The installation wiki mentions that if the whole system locks up at that point then its a kernal crash, but every other part of ubuntu works fine - apart from ndiswrapper. I'm confused as to what the root of the problem could be.

I checked "dmesg" to troubleshoot and heres the last few lines:
I'm at a loss as to what any of it means :(

```
[4299709.855000] Call Trace:
[4299709.855000]  [<f8d8aaa7>] wrap_kmalloc+0x3d/0x78 [ndiswrapper]
[4299709.855000]  [<f8d8d79d>] NdisMInitializeTimer+0xf/0x2c [ndiswrapper]
[4299709.855000]  [<f8d92e82>] miniport_init+0x57/0x5b [ndiswrapper]
[4299709.855000]  [<f8d89878>] ndiswrapper_add_one_usb_dev+0x8f/0x154 [ndiswrapp er]
[4299709.855000]  [<f88e804f>] usb_probe_interface+0x49/0x60 [usbcore]
[4299709.855000]  [<c01ec222>] driver_probe_device+0x36/0x54
[4299709.855000]  [<c01ec2fa>] driver_attach+0x39/0x6a
[4299709.855000]  [<c01ec680>] bus_add_driver+0x5e/0x80
[4299709.855000]  [<c01ec9e1>] driver_register+0x23/0x25
[4299709.855000]  [<f88e810d>] usb_register+0x42/0x87 [usbcore]
[4299709.855000]  [<f8d8a5e5>] register_devices+0x43a/0x4d2 [ndiswrapper]
[4299709.855000]  [<c019cda0>] copy_from_user+0x34/0x58
[4299709.855000]  [<f8d8a6b3>] wrapper_ioctl+0x36/0xaa [ndiswrapper]
[4299709.855000]  [<c015312c>] do_ioctl+0x48/0x4e
[4299709.855000]  [<c0153387>] vfs_ioctl+0x172/0x17f
[4299709.855000]  [<c01533da>] sys_ioctl+0x46/0x60
[4299709.855000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4299709.855000] Code: fc 00 00 00 00 8b 45 08 89 45 f8 c7 45 fc 00 00 00 00 eb 09 8b 4d fc 83 c1 01 89 4d fc 8b 55 fc 3b 55 0c 73 0b 8b 45 f8 03 45 fc <c6> 00 00 eb e4 8b e5 5d c2 08 00 cc cc 55 8b ec 83 ec 0c 8b 45
[4299709.855000]  <3>ndiswrapper (wrapper_init:1534): loadndiswrapper failed (11 ); check system log for messages from 'loadndisdriver'
[4299709.864000] usbcore: deregistering driver ndiswrapper
[4299719.023000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4299719.023000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

I also download ndisgtk using automatix which is showing the driver and hardware as 'present'.

If anyone has any advice they could give me or a thread with more info etc then I'd be extremely grateful. Every aspect of ubuntu and linux intrests me grately and I'd love to get this problem sorted soon :)

If I've left anything out, or anything that I need to clarify; let me know. I'll be monitering this thread so I'll probably reply within a few minutes.

Thanks in advance guys!

- David

---

