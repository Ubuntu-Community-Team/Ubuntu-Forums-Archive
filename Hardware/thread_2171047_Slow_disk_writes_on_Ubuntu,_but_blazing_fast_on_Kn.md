---
title: "Slow disk writes on Ubuntu, but blazing fast on Knoppix?"
date: 2013-08-28
forum: Hardware
---

### Post by maiden_taiwan on 2013-08-28
My brand-new Ubuntu desktop (12.04 LTS) has extremely slow write speed (1 MB/sec) on **all** its hard drives. However, if I *boot on Knoppix 7.2 *(kernel 3.9), the speed on all drives is immediately fixed, increasing to 100 MB/sec. Can anybody help me fix the speed under Ubuntu?
 
The slowness happens on an internal Western Digital HD, an internal SSD RAID pair (3ware RAID card), and external hard drives using USB 3.0, Firewire, and eSATA, all using ext4. Literally every storage device I can connect.

I also tried Ubuntu 13.04 and (prerelease) 13.10 Live CDs on the same system, and they had the same slowness as 12.04.

This is a very fast computer (8 cores, 32 GB RAM, SSD boot drive), so system horsepower is not the problem. Nevertheless, a 20-megabyte file takes 15 seconds to copy under Ubuntu, but only 0.03 seconds under Knoppix.

I have already checked:

[LIST]
[*]dmesg, and I didn't notice anything bad (see the [full output]("http://www.blazemonger.com/dmesg.txt")). However, I am not a dmesg expert.
[*]hdparm: Ubuntu and Knoppix had exactly the same settings except for -Q, and when I changed it on Ubuntu to match Knoppix, it did not help the speed. However, I am not an hdparm expert. Here are the WD disk parameters:
[/LIST]

```
$ sudo hdparm -acdgkmurABCMNQW /dev/sda
/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 364801/255/63, sectors = 5860533168, start = 0
 look-ahead    =  1 (on)
 APM_level      = not supported
 drive state is:  active/idle
 acoustic      = not supported
 max sectors   = 5860533168/5860533168, HPA is disabled
 queue_depth   = 31  (Knoppix had value = 1, but changing on Ubuntu didn't help)
 write-caching =  1 (on)

```

Hardware:
[LIST]
[*]CPU: Intel Core i7-3930K Sandy Bridge-E 3.2GHz (8 cores)
[*]Motherboard: ASUS P9X79
[*]RAID card: 3ware 9750-4i 6Gb/s 4 Port Internal
[*]Boot drive: Two SSDs (Crucial m500 960GB in RAID 1)
[*]Second drive: Western Digital Red 3TB (directly on SATA controller, not on RAID card)
[*]External drive: Fantom 4TB drive with USB3, Firewire, and eSATA interfaces
[/LIST]

I am really at my wits' end and would appreciate *any* help or guidance! Thank you very much.

---

### Post by maiden_taiwan on 2013-08-29
I pulled out the RAID card and booted on Ubuntu 13.04 Live CD --- the slowness is still there.

---

### Post by maiden_taiwan on 2013-08-30
Problem solved!

I switched from the 32-bit PAE kernel to a 64-bit kernel (Ubuntu 13.04), and disk writes are now fast.

---

