---
title: "USB Won't mount no matter what i do"
date: 2010-05-30
forum: Hardware
---

### Post by markzins on 2010-05-30
i upgraded from ubuntu 9.10 karmic to 10.4 lucid, and i have a usb flash drive that i was able to mount yesterday but not now, like it sometimes works and sometimes doesn't. 
I have looked through many forums but have found no solution that has worked. 

when i type in lsusb:


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 013: ID 07d1:3a08 D-Link System predator Bootloader Download
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

when i type dmesg:

[  478.663477] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  478.665948] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  493.783031] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  495.863105] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  506.368013] wlan0: no IPv6 routers present
[  675.511644] usb 1-6: USB disconnect, address 12
[  678.188026] usb 1-5: new high speed USB device using ehci_hcd and address 14
[  678.321941] usb 1-5: configuration #1 chosen from 1 choice
[ 1094.812585] usb 1-5: USB disconnect, address 14
[ 1097.428018] usb 1-5: new high speed USB device using ehci_hcd and address 15
[ 1097.561145] usb 1-5: configuration #1 chosen from 1 choice
[ 1366.071708] usb 1-5: USB disconnect, address 15
[ 1367.760038] usb 1-6: new high speed USB device using ehci_hcd and address 16
[ 1367.893832] usb 1-6: configuration #1 chosen from 1 choice

i have tried to manually mount it
i type 
sudo fdisk -l


Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5219    41916584+   7  HPFS/NTFS
/dev/sda2            5219        9734    36265985    5  Extended
/dev/sda5            5219        9572    34965504   83  Linux
/dev/sda6            9572        9734     1299456   82  Linux swap / Solaris

can anyone give me some help?

---

### Post by efflandt on 2010-05-30
Did you disconnect it when something had not finished writing to it (without umounting it or safely remove)?  Does it still work on any other computer or OS?  What filesystem(s) were on it?

---

### Post by markzins on 2010-05-31
It works fine on my laptop which has the same ubuntu version, so I know that i didn't accidentally disconnect when it was writing data. I know it is a 2gb sandisk that just has basic pictures and music on it, i have never tried to make a start-up disk with it. Its like i knows its there but i just doesn't want to mount it.

---

### Post by dcrich0893 on 2010-10-09
Hi All,

I'll preface my question by saying that.......

1.  I am new to linux but not new to computers
2.  I have been researching this USB question on numerous (and I "do mean" numerous) on-line forums for almost a week now and.....
3.  I am convinced that there is NO definitive answer to this question 

All I have seen are "might be's"................

Is there a "real" answer to the problem?

I am running Ubuntu 10.4 on a IBM Thinkpad X40.  The USB ports worked fine prior to Ubuntu and I have (on several occasions) tested the USB stick in other machines and it works just fine:confused::confused::confused:

---

