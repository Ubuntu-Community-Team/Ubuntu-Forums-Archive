---
title: "[SOLVED] how to mount external DAC: appears in dmesg but not fdisk"
date: 2008-07-18
forum: Hardware
---

### Post by conphuzed on 2008-07-18
dmesg

```
[   78.603818] wlan0: RX AssocResp from 00:17:9a:d5:15:46 (capab=0x471 status=0 aid=4)
[   78.603822] wlan0: associated
[   78.609931] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   98.196613] wlan0: no IPv6 routers present
[  335.136658] usb 4-1: USB disconnect, address 2
[  390.991044] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  391.190752] usb 4-1: configuration #1 chosen from 1 choice
[  391.222656] input: Burr-Brown from TI               USB Audio DAC    as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.2/input/input10
[  391.278796] input,hidraw0: USB HID v1.00 Device [Burr-Brown from TI               USB Audio DAC   ] on usb-0000:00:1d.1-1
[ 1016.381917] npviewer.bin[7408]: segfault at f5b7c030 rip f7970540 rsp ffd9100c error 4

```

it's the 'USB Audio DAC'

fdisk

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x381ff000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19574   157228123+   7  HPFS/NTFS
/dev/sda2           19575       30401    86967877+   5  Extended
/dev/sda5           19575       29955    83385351   83  Linux
/dev/sda6           29956       30401     3582463+  82  Linux swap / Solaris
```

how to mount it?

---

### Post by conphuzed on 2008-07-28
just fyi

i ended up solving this by blacklisting internal audio like most people seem to do. initially, i had to blacklist or unblacklist and reboot to switch between external DAC and onboard audio, but after a while, i have no idea why, the system began switching automatically. i.e. it seems it doesn't matter whether i blacklist onboard audio, when i plug in the DAC it works, when i unplug it onboard sound works again.

but yes to get the DAC to work intially i had to blacklist onboard audio

---

