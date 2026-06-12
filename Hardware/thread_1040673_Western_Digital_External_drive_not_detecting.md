---
title: "Western Digital External drive not detecting"
date: 2009-01-15
forum: Hardware
---

### Post by sxjast on 2009-01-15
Hello,

I just got my Western Digital My Passport External drive and connected it. My ubuntu desktop didn't detect it and I don't see it mounted. Do I need to install any drivers?

Thanks,
sxjast

---

### Post by mtbsoft on 2009-01-16
I had some similar issues with a WD MyBook a few months back.  Turned out that the device was being detected, just not auto-mounted. 

Try plugging it in, wait a few seconds then check your log file (/var/log/messages) - you may find some messages at the end related to USB devices and disk devices which indicate that it is loaded and which device you need to mount.

Sorry to be a bit vague but, as mine now works I cannot tell you the exact nature of those messages as they're not in my logs any more.

---

### Post by sxjast on 2009-01-16
I don't have log directory under /var. I have flash drives and they work fine. It's just this external hard drive, not working.

---

### Post by taurus on 2009-01-16
Make sure the drive is plugged in.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by sxjast on 2009-01-17
I have the drive connected and here is the output of the above command.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7f3b7f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+  82  Linux swap / Solaris
/dev/sda2            1021       38912   304367490    f  W95 Ext'd (LBA)
/dev/sda3           38913       38913        8032+  83  Linux
/dev/sda5            1021        4508    28017328+  82  Linux swap / Solaris
/dev/sda6            8670       16318    61440561   82  Linux swap / Solaris
/dev/sda7           16319       23967    61440561   82  Linux swap / Solaris
/dev/sda8           23968       31616    61440561   82  Linux swap / Solaris
/dev/sda9           31617       38912    58605088+  83  Linux
/dev/sda10           4509        8669    33423201   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2009-01-17
What about the output of this command?

```
dmesg | tail
```
And by the way, do you think you have enough swap partitions?  I count six total!

```
free -m
```

---

### Post by sxjast on 2009-01-17
Thank you so much for looking at my issue.

Output of "dmesg | tail" is

[   35.132940] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   35.473757] NET: Registered protocol family 17
[   43.304220] NET: Registered protocol family 10
[   43.305587] lo: Disabled Privacy Extensions
[   53.784006] eth0: no IPv6 routers present
[  123.671302] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.3 DST=192.168.0.255 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56314 DPT=161 LEN=54 
[  125.700726] ppdev0: registered pardevice
[  125.748728] ppdev0: unregistered pardevice
[  126.851277] ppdev0: registered pardevice
[  126.900018] ppdev0: unregistered pardevice

and the output of "free -m" is

             total       used       free     shared    buffers     cached
Mem:          5975        795       5179          0         26        280
-/+ buffers/cache:        489       5486
Swap:        60000          0      60000

---

