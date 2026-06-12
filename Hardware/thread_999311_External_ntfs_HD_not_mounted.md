---
title: "External ntfs HD not mounted"
date: 2008-12-01
forum: Hardware
---

### Post by Ber P on 2008-12-01
I've just installed 8.10 (fresh install), and have problems mounting my external HD. In 7.10, I just pluged it in, and it was mounted right away. In 8.10 when I plug it in, the 'active' light on the HD stays on, and it makes not-so-comfortable sounds every now and then.

lsusb give me this result:
```
Bus 004 Device 002: ID 046d:c503 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0d49:5020 Maxtor Mobile Hard Disk Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The drive is seen as Device 008.

sudo fdisk -l dosen't show the drive at all.

I thought about force mounting it, but how do I do that, when I can't see the 'name' (sdb1 or something)?

Otherwise the usb connections works fine (tried with a usb pen - no problems).

The HD works fine in windows, and I made sure to safely remove it, in order not to damage the NTFS journal

---

### Post by cariboo on 2008-12-01
In a Applications-->Accessories-->Terminal type:

```
dmesg | tail -n 10
```

When you plug your external drive in, this will give you an indication of what drive to mount manually. the above command will print out the last ten lines of dmesg.

Jim

---

### Post by Ber P on 2008-12-02
```
:~$ dmesg | tail -n 10
[  342.724536] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[  342.724551] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  344.013446] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[  344.013460] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  345.219393] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[  345.219407] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  346.400460] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[  346.400474] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  347.573159] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[  347.573172] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information

```

does this mean it is sdb? Can I now ```
sudo mount -t ntfs-3g /dev/sdb /media/sdb1 -o force

```
Is it the correct switches?

Btw. if I leave the HD pluged in, then I'll hang at boot. Hopefully just because it is not recognized. :confused:

---

### Post by Ber P on 2008-12-02
hmmmmm..... have found tons of threads about this issue, but no answers. Is this a bug in kernel 2.6.27-9?

---

### Post by razy60 on 2008-12-02
when you originally formated the drive did you use windows, if you did was it mounted as primary drive or extended drive, as I don't think that you can see a windows formated extended ntfs drive in Ubuntu, you need to format it as a primary drive.

---

### Post by Ber P on 2008-12-02
I've not formated it myself (used device). But it's not the drive thats the problem. I used it with 7.10 without any problems.

---

