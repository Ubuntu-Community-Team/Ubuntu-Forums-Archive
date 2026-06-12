---
title: "Problem no mount pendrive USB 2.0 in Ubuntu 12.04.2 but if mount USB 3.0"
date: 2013-05-30
forum: Hardware
---

### Post by dantexier on 2013-05-30
I have 3 usb port, my laptop is VAIO Sony T Series Ultrabook w/Touchscreen and installed Ubuntu 12.04.2. So, My usb port 3.0 works correctly and the others usb ports 2.0. doesn't work, somebody could help me?


These are my data:
dmesg | tail -20


[    3.514170] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    3.514235] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    3.942361] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[    5.018566] wlan0: authenticate with 00:23:69:2e:b3:ff
[    5.023118] wlan0: send auth to 00:23:69:2e:b3:ff (try 1/3)
[    5.026671] wlan0: authenticated
[    5.033395] wlan0: associate with 00:23:69:2e:b3:ff (try 1/3)
[    5.036104] wlan0: RX AssocResp from 00:23:69:2e:b3:ff (capab=0x411 status=0 aid=2)
[    5.036176] wlan0: associated
[    5.036963] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.300949] CPU1: Package power limit notification (total events = 1)
[    6.300953] CPU3: Package power limit notification (total events = 1)
[    6.300954] CPU2: Package power limit notification (total events = 1)
[    6.300955] CPU0: Package power limit notification (total events = 1)
[    6.312949] CPU1: Package power limit normal
[    6.312950] CPU0: Package power limit normal
[    6.312952] CPU2: Package power limit normal
[    6.312953] CPU3: Package power limit normal
[  307.467934] audit_printk_skb: 39 callbacks suppressed
[  307.467944] type=1400 audit(1369932859.268:2


lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:002d Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0489:e036 Foxconn / Hon Hai 
Bus 001 Device 005: ID 05ca:18c4 Ricoh Co., Ltd 


fdisk -l
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
Disk /dev/sda: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders, total 351651888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   351651887   175825943+  ee  GPT
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.
Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd82510d6
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    46905263    23452631+  ee  GPT


uname -a
Linux TexierLinux 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

