---
title: "No storage device recognized"
date: 2016-10-24
forum: Hardware
---

### Post by freimann2 on 2016-10-24
Hi

I recently upgraded to Ubuntu 16.04 and tried to use my memory stick, but it's not recognized. I know the memory stick is okay, because I tried it with another computer and it worked fine. Also, when I tried to read my SD card then that also wasn't recognized so it would seem that not one storage device is recognized. They have worked before.

Commands* lsusb* and *lsblk *show these outputs (with USB memory stick plugged in):

```

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
ron@ron-Inspiron-N5040:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0  39,2M  0 part 
&#9500;&#9472;sda2   8:2    0     5G  0 part 
&#9492;&#9472;sda3   8:3    0 460,7G  0 part /
sr0     11:0    1  1024M  0 rom
```

I also tried restarting the computer with and without memory stick but no luck.

---

### Post by freimann2 on 2016-11-09
Anyone?

From other threads I'v also read that command sudo dmegs  -c can give useful output, so I ran that command (USB memory stick  unplugged).

```


[267956.183824] pciehp 0000:00:1c.2:pcie04: Device 0000:13:00.0 already exists at 0000:13:00, cannot hot-add
[267956.183826] pciehp 0000:00:1c.2:pcie04: Cannot add device at 0000:13:00
[267956.183843] pciehp 0000:00:1c.1:pcie04: Device 0000:12:00.0 already exists at 0000:12:00, cannot hot-add
[267956.183844] pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:12:00
[267956.285163] pciehp 0000:00:1c.2:pcie04: Device 0000:13:00.0 already exists at 0000:13:00, cannot hot-add
[267956.285168] pciehp 0000:00:1c.2:pcie04: Cannot add device at 0000:13:00
[267956.285173] pciehp 0000:00:1c.1:pcie04: Device 0000:12:00.0 already exists at 0000:12:00, cannot hot-add
[267956.285177] pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:12:00


```
 
and
```


[267956.557158] usb 2-1.2: new low-speed USB device number 58 using ehci-pci
[267956.629191] usb 2-1.2: device descriptor read/64, error -32
[267956.805230] usb 2-1.2: device descriptor read/64, error -32
[267956.981302] usb 2-1.2: new low-speed USB device number 59 using ehci-pci
[267957.054057] usb 2-1.2: device descriptor read/64, error -32
[267957.229816] usb 2-1.2: device descriptor read/64, error -32
[267957.405357] usb 2-1.2: new low-speed USB device number 60 using ehci-pci
[267957.813456] usb 2-1.2: device not accepting address 60, error -32
[267957.885521] usb 2-1.2: new low-speed USB device number 61 using ehci-pci
[267958.293590] usb 2-1.2: device not accepting address 61, error -32
[267958.293774] usb 2-1-port2: unable to enumerate USB device


```

 I got an output, which clearly shows some kind of a error, but I couldn't find out what this error code 32 means. Has somebody any ideas?

---

### Post by freimann2 on 2016-12-03
Really, is there nobody who knows anything about the issue or what the problem could be?

---

### Post by Bucky Ball on 2016-12-03
Obviously not. You can bump your thread if no one responds within 12 hours to get it back to the top of the new posts list and in sight. 

All I could suggest is were these devices unmounted/ejected correctly from the Win box? Try plugging them into Windows again and eject them correctly then give it another go. Just a thought.

Also, if your SD card is of the larger variety, you will need to install exfat-utils and exfat-fuse in Ubuntu to use it. You will find them both in your package manager or install from a terminal if you're up to it.

---

### Post by freimann2 on 2016-12-09
Treyed ejecting them correctly, no help. 

Also, I already have exfat-utils and fuse installed so it cannot be bacuse of that. But thanks for the help! 

I guess I have to start narrowing it down myself. Just hoping that somebody can confirm that they don't have the same problem with their upgrade to 16.04 so I would know that it's not because of that.

---

