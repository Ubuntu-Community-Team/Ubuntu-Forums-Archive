---
title: "USB ports just stopped working"
date: 2015-11-22
forum: Hardware
---

### Post by sfk2 on 2015-11-22
Not that long ago, the usb ports on my laptop just stopped mounting anything I plug in. It doesn't seem to matter what it is or which port I use. the devices seem to be recognized, but it gets hung up and wont mount.

I haven't been able to figure this out and would really love some help.

lsusb:
```

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:5682 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Repetitive output of dmesg is attached.

fdisk -l:

```
Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: CD7E5D5C-0446-4B3A-9315-6A55587857A1

Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1026047   1024000  500M EFI System
/dev/sda2    1026048   1107967     81920   40M unknown
/dev/sda3    1107968   7399423   6291456    3G Microsoft basic data
/dev/sda4    7399424 216905727 209506304 99.9G Linux filesystem
/dev/sda5  216905728 250068991  33163264 15.8G Linux swap


```

Again, any and all help would be greatly appreciated.

---

### Post by weatherman2 on 2015-11-22
Can you still boot off USB?  Or, do still have a Windows partition to boot into?  In other words, do the USB ports still work in Windows or are they recognized by your computer's firmware (BIOS) when you try to boot from USB?

Just trying to understand whether it's a hardware problem or an OS problem.  Clearly, if you can still see USB devices in Windows it's not a hardware problem.

---

### Post by medic0079 on 2015-11-23
I have exactly the same problem I can boot with device inserted and it will recognize but if I unplug and replug it will not recognize any ideas?

---

