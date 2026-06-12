---
title: "Unable to get printer to work (cable not detected, lsusb doesn't detect)"
date: 2015-04-16
forum: Hardware
---

### Post by sollinger on 2015-04-16
Hello all,

I have two printers and I'd love to get at least one working. One is the dreaded Canon LBP6000 which everyone hates. The other is the HP Laserjet 2300L which worked for one evening and then promptly stopped working. I think I have read every single how-to on here, but I'm really frustrated because I can't seem to have the solutions work.

I'm running Ubuntu 14.10. 

Typically what has happened is after running every variation of a command to get the LBP installed, I'd reboot and nothing would work again. I had previously installed the 2300L with no problems and even printed things but then it stopped working. Since I can't detect it in lsusb (other usb devices like my mouse and phone are detected), I don't even know how to begin to trouble shoot. I thought it was the cable, but a brand new cable also doesn't show anything.

As a start here is what I see with lsusb:
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 008: ID 5986:055c Acer, Inc 
Bus 003 Device 007: ID 8087:07dc Intel Corp. 
Bus 003 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 017: ID 04a9:271a Canon, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
Neither of the printers show up.

When I run this (and plug and unplug the Canon LBP6000): tail -f /var/log/syslog
```
root@gazelle:/home/sam# tail -f /var/log/syslog
Apr 16 14:51:08 gazelle kernel: [ 1094.249755] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
Apr 16 14:51:08 gazelle kernel: [ 1094.249756] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
Apr 16 14:51:08 gazelle kernel: [ 1094.249758] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
Apr 16 14:51:08 gazelle kernel: [ 1094.249759] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
Apr 16 14:51:08 gazelle kernel: [ 1094.249760] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
Apr 16 14:51:08 gazelle kernel: [ 1094.249761] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
Apr 16 14:51:08 gazelle kernel: [ 1094.249763] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Apr 16 14:51:08 gazelle wpa_supplicant[1572]: wlan0: WPA: Key negotiation completed with 88:dc:96:1b:e2:a2 [PTK=CCMP GTK=TKIP]
Apr 16 14:51:08 gazelle wpa_supplicant[1572]: wlan0: CTRL-EVENT-CONNECTED - Connection to 88:dc:96:1b:e2:a2 completed [id=0 id_str=]
Apr 16 14:51:08 gazelle NetworkManager[994]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 16 14:51:22 gazelle kernel: [ 1107.913203] usb 3-3: USB disconnect, device number 17
Apr 16 14:51:22 gazelle kernel: [ 1107.913560] usblp0: removed
Apr 16 14:51:22 gazelle udev-configure-printer: remove /devices/pci0000:00/0000:00:14.0/usb3/3-3
Apr 16 14:51:27 gazelle kernel: [ 1112.793206] usb 3-3: new high-speed USB device number 18 using xhci_hcd
Apr 16 14:51:27 gazelle kernel: [ 1112.926536] usb 3-3: New USB device found, idVendor=04a9, idProduct=271a
Apr 16 14:51:27 gazelle kernel: [ 1112.926539] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 16 14:51:27 gazelle kernel: [ 1112.926541] usb 3-3: Product: Canon CAPT USB Device
Apr 16 14:51:27 gazelle kernel: [ 1112.926542] usb 3-3: Manufacturer: Canon
Apr 16 14:51:27 gazelle kernel: [ 1112.926543] usb 3-3: SerialNumber: 0000A2D8QN87
Apr 16 14:51:27 gazelle kernel: [ 1112.927410] usblp 3-3:1.0: usblp0: USB Bidirectional printer dev 18 if 0 alt 0 proto 2 vid 0x04A9 pid 0x271A
Apr 16 14:51:27 gazelle mtp-probe: checking bus 3, device 18: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3"
Apr 16 14:51:27 gazelle mtp-probe: bus: 3, device: 18 was not an MTP device
Apr 16 14:51:27 gazelle udev-configure-printer: add /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0
Apr 16 14:51:27 gazelle udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0
Apr 16 14:51:29 gazelle wpa_supplicant[1572]: wlan0: CTRL-EVENT-SCAN-STARTED 


```

Zero feedback from the HP 2300L. 

I have cups installed. And a test page sent to the LBP6000 Canon shows this:
```
[TABLE]
[TR]
[TH]Description:[/TH]
[TD]Canon LBP6000/LBP6018 CAPT[/TD]
[/TR]
 [TR]
[TH]Location:[/TH]
[TD]gazelle[/TD]
[/TR]
 [TR]
[TH]Driver:[/TH]
[TD]Canon LBP6000/LBP6018 CAPT (US) (grayscale, 2-sided printing)
[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]ccp://localhost:59687[/TD]
[/TR]
 [TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=na_letter_8.5x11in sides=one-sided[/TD]
[/TR]
[/TABLE]

```

And this:
```
[TABLE="class: list"]
[TR]
[TD][Canon-LBP6000-LBP6018-CAPT]("http://localhost:631/printers/Canon-LBP6000-LBP6018-CAPT")-104 [/TD]
 [TD]Unknown [/TD]
 [TD]Withheld [/TD]
 [TD]1k [/TD]
 [TD]Unknown [/TD]
 [TD] processing since
Thu 16 Apr 2015 02:42:15 PM PDT [/TD]
[/TR]
[/TABLE]

```
 
I know I shouldn't have bought the LBP6000, but with a  nonworking HP 2300L as well, I just can't keep getting more printers. I'd like one to work. I'd love for any help in pointing me in the right direction.

Thank you.
Sam

---

### Post by Vladlenin5000 on 2015-04-16
If the printer doesn't show up and you tested already in other USB ports and/or other computers then, considering the cable has also been ruled out, the printer is kaput. There's no software remedy for that.
According to you it worked but then stopped out of the blue. In most of the (rare) cases it is a software issue due to some update or other changes but the printer is still listed (lsusb). Yours isn't...

---

### Post by pdc on 2015-04-17
further to vladlenin's comments; 

another issue is ............ 2 printers............ both usb connected?

The reason it can be a problem is that with a single usb printer, it will be set up as lp0 ........................... that's fine ...............and if you set up a second printer ............ it will lp1 ..................but you need to ensure lp0 is turned on first; and then lp1 ............. otherwise the system will be confused ..

..........one can solve it with a udev rule specifying which is which  .............. you just need to write the rule

_______________

the LBP6000 uses Canon's CAPT driver; it works well for us on an LBP series; however that is for 32bit: Canon are working on a new 64bit for 14.04 but it is not released yet I understand .......... please tell us you have a 32bit system 

__________________

I can see your connection is set up for the LBP6000 as > ccp://localhost:59687            ..........that won't work with ubuntu  ...............it needs to be > ccp://localhost:[COLOR="#FF0000"]59787[/COLOR]

........ you have the CAPT driver installed already?

---

### Post by sollinger on 2015-04-17
Vladlenin5000  and pdc: Thank you for responding. After reading Vladlenin5000's comment, I concluded that indeed the printer was kaput and Canon's setup has giving me a headache for months. I purchased a Samsung-C460-Series that worked out the box with no headaches, extra reading, or anything else. Just worked. 

Really appreciate the feedback. pdc, yes I did have  CAPT installed. I'll try to fiddle some more with the Canon after work and change the port issue as you mentioned. But I'm not putting much faith that it will work.

---

