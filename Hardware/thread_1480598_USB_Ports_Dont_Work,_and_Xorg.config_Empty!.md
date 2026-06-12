---
title: "USB Ports Dont Work, and Xorg.config Empty!"
date: 2010-05-11
forum: Hardware
---

### Post by nsteger123 on 2010-05-11
My System:
Ubuntu 10.04 Lucid Lynx (64-bit)
Toshiba Satellite A505-6004
4GB DDR3 RAM
Core i3
Intel GMA HD
RTL8191SE with Official Linux Drivers installed.
etc...

1) My xorg.config file is empty. Its located in the X11 folder.
   a) Trying to enable 2 finger scrolling.
2) My USB ports do not work. They do not detect Flash Drives.
   a) They are Sandisk Cruzer Micro, one 8GB and one 2GB. Both are formatted to FAT32 (I think!)

Other:
**sudo fdisk -1**
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc38deb05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       55619   445218816    7  HPFS/NTFS
/dev/sda3           55619       59443    30718977    f  W95 Ext'd (LBA)
/dev/sda4           59443       60802    10910720   17  Hidden HPFS/NTFS
/dev/sda5           55619       59443    30718976   83  Linux

```

**lsusb (With drives plugged in)**
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**dmesg**
```
[   43.064371] usb 1-1: device not accepting address 4, error -110
[   43.183451] usb 1-1: new high speed USB device using ehci_hcd and address 5
[   43.991946] eth0: no IPv6 routers present
[   53.596605] usb 1-1: device not accepting address 5, error -110
[   53.596627] hub 1-0:1.0: unable to enumerate USB device on port 1
[   53.756189] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   54.575465] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   58.743330] ehci_hcd 0000:00:1d.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   69.286096] usb 2-1: device not accepting address 2, error -110
[   69.405771] usb 2-1: new high speed USB device using ehci_hcd and address 3
[   84.498132] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   84.936806] usb 2-1: device not accepting address 3, error -110
[   85.055272] usb 2-1: new high speed USB device using ehci_hcd and address 4
[   95.469653] usb 2-1: device not accepting address 4, error -110
[   95.589346] usb 2-1: new high speed USB device using ehci_hcd and address 5
[  106.002435] usb 2-1: device not accepting address 5, error -110
[  106.002460] hub 2-0:1.0: unable to enumerate USB device on port 1

```

All updates are installed, and upgraded to latest BIOS.

If you need any other info, just ask and i will gladly post it.
Thanks in advance!

EDIT: Also, why doesn't Evolution Mail notify me of mail in the background?

EDIT: Wireless Info:
**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:3a:c9:d7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe3a:c9d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63013145 (63.0 MB)  TX bytes:3977048 (3.9 MB)
          Interrupt:33 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32906688 (32.9 MB)  TX bytes:32906688 (32.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:a9:fd:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:ffffc90005088000-ffffc90005088100 

```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Nothing shows up in the Hardware Drivers

---

### Post by wankel on 2010-05-11
With KMS (kernel mode settings), there is no xorg.conf needed for X to run properly. I do not know about the touch pad, but the absense of xorg.conf as such, is not an error.

The -110 error is a broken USB memory stick, I am afraid. I have a bunch of those that would work at work (Microsoft), but not at home. They give the same error, if I recall correctly. (There are some that work fine at home but not at work, so I don't have all answers here either ;-) )

---

### Post by nsteger123 on 2010-05-11
Well, they're definitely not broken as they work in Windows 7. It must be a problem with Ubuntu, as none of my USB devices work such as my Archos 5 Internet Tablet.

---

### Post by wankel on 2010-05-11
"definitely not broken" got gray borders. When I delved into it, it turned out to have to do with stricter timings on Linux or laxer requirements from Microsoft. 

You can see in the log that the USB port works, it recognizes that something is inserted anyway. I am sorry that I can not remember the error code; a quick google gave too varied results for me to remember clearly.

My browser messes up the text (no reflow) so the last bits of every line disappear into the air next to my laptop; you say that none of your USB devices work, such as an internet... Is that a USB wifi or 3G something, or at least, something else than a memory device? 

I guess you're using a standard kernel, else it could be something is missing there?

Have you tried a webcam or such? I am just poking along the way I would try myself; if it is useless advice please be not offended.

---

### Post by nsteger123 on 2010-05-11
No, the only USB devices i have tried were the (2) Flashdrives and my Archos 5 Android. The Archos charges but does not connect. The FlashDrives have an orange light, and it blinks once and stays off.

As for the wireless, it's an integrated card. Its the RTL8191SE (Realtek).

I would love to try the webcam, but I haven't tried using it yet nor looking for drivers.

---

### Post by nsteger123 on 2010-05-16
Bump!

---

