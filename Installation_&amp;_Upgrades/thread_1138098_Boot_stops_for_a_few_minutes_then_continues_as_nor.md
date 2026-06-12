---
title: "Boot stops for a few minutes then continues as normal"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Hoeye on 2009-04-26
I upgraded from 8.10 to 9.04 the day before yesterday. Since the upgrade my boot process is taking ages...

after a few seconds the splash screen comes up. The bar progresses a bit then freezes for a loooooong time (few minutes) then continues as normal.

Searching the forum i found that you experts need for example the dmesg output. well, here it goes...

I found 2 parts in the dmesg that slowed things down. I found:

[    3.296447] EXT3-fs: mounted filesystem with ordered data mode.
[    3.324844] usb 3-1: configuration #1 chosen from 1 choice
[    4.064424] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000358e65e]
[   14.049251] udev: starting version 141
[   14.385399] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   14.385521] usbcore: registered new interface driver btusb

a delay of 10 seconds.... ( I guess )

then later:

[   16.819197]  [<c0163fc8>] ? sys_init_module+0x88/0x1b0
[   16.819202]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[   16.819206]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   16.819212] Code: 15 b8 5f c8 8b 55 90 8b 82 2c 01 00 00 89 5c 24 04 c7 04 24 b8 23 f1 f7 89 44 24 08 e8 f8 b7 5f c8 66 90 8b 45 90 e8 40 fd ff ff <8b> 5d f4 31 c0 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 4d 90 8b 71 
[   16.819256] EIP: [<f7f052c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ESP 0068:f6061c54
[   16.819270] ---[ end trace bb07fc4914231bf8 ]---
[  195.230994] lp: driver loaded but no devices found
[  195.300117] it87: Found IT8705F chip at 0xa10, revision 3
[  195.509279] Adding 2016116k swap on /dev/sda6.  Priority:-1 extents:1 across:2016116k
[  196.046821] EXT3 FS on sda5, internal journal

This is a delay of a couple of minutes... but what happens is unclear to me...

Can anyone help?

---

### Post by Hoeye on 2009-04-26
I found the bootchart file... maybe it can give more help....

---

### Post by Hoeye on 2009-04-26
I'm still working on it...

found a thread somewhere that advised to kill the tv-card driver by blacklisting it. This worked fine! 

Boot time now down to 30 secs. not bad... not bad at all... 

Now I'm wondering if I can get rid of the 10 sec delay in the beginning... that would make boot REALLY fast...

Suggestions?

---

### Post by Triptol on 2009-04-26
Don't think you can drop those 10 seconds (although that seems a bit long). It seems that the kernel is initializing your usb devices and that just takes some time. You could, of course, recompile a kernel without usb, but I don't think that would make you happy.

---

### Post by Hoeye on 2009-04-26
Right - I've been trying some things, but nothing happens. I think I leave it as it is... anyhow 30 secs boot is quite ok... my XP took more than 2 minutes...

Thx anyway!

---

### Post by ssam on 2009-04-26
the numbers in dmesg are the time since boot in seconds. so the delay is between 4 and 14 seconds. ieee1394 is firewire, if you are not using any firewire devices you could black list that.

i guess the module name is ieee1394, but you can check what modules you have loaded currently by running
```
lsmod
```

---

### Post by Hoeye on 2009-04-26
I indeed have a ieee1394 line in my lsmod

```
ieee1394               94660  2 sbp2,ohci1394
```

I think I can black-list it, but I read somewhere that ieee1394 is needed for USB. Can anyone confirm this? Or is it safe to black-list...

---

