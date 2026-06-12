---
title: "Kobo touch ereader doesn't mount"
date: 2012-10-12
forum: Hardware
---

### Post by jfca283 on 2012-10-12
Hi
i have a kobo touch ereader. It used to work fine but since i upgraded its firmware i can't access to it as a common usb stick. However, the device is charging the battery when is plugged to my notebook.
Here is fdisk -l with it connected
```
juan@Cecca-PC:~$ sudo fdisk -l
[sudo] password for juan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf40ae7c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   108955647    54374400    7  HPFS/NTFS/exFAT
/dev/sda3       108957694   976771071   433906689    5  Extended
/dev/sda5       108957696   970653695   430848000   83  Linux
/dev/sda6       970655744   976771071     3057664   82  Linux swap / Solaris

``` So you see, the system doesn't recognise it like a usb storage device. Here's my dmesg output
```
juan@Cecca-PC:~$ dmesg |tail
[21578.646745] cfg80211: Disabling freq 2472 MHz
[21578.646748] cfg80211: Disabling freq 2484 MHz
[21578.646757] cfg80211: Regulatory domain changed to country: US
[21578.646761] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[21578.646767] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[21578.646772] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[21578.646777] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[21578.646783] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[21578.646788] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[21578.646793] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```Any idea? Thanks for your help

---

