---
title: "USB flash drive wont work"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by ashrack on 2006-10-10
On school we have 4 DAPPER DRAKES. And on all of them USB flash works! But there is one USB drive 512MB that works great on Windows but in Dapper Drake it wont mount it. The firm is CANYON 512MB and in windows it gets 2 partitions. Below is the error log:
**q@zavod:~$ tail -f /var/log/messages**
```
oct 10 16:30:55 localhost kernel: [17179834.936000] sda : status=0, message=00, host=1, driver=00
Oct 10 16:30:55 localhost kernel: [17179834.936000] sda : sense not available.
Oct 10 16:30:55 localhost kernel: [17179834.940000] sda: Write Protect is off
Oct 10 16:30:55 localhost kernel: [17179834.940000] sd 0:0:0:1: Attached scsi removable disk sda
Oct 10 16:30:55 localhost kernel: [17179835.052000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Oct 10 16:31:14 localhost kernel: [17179853.596000] usb 1-1: new full speed USB device using uhci_hcd and address 4
Oct 10 16:31:32 localhost kernel: [17179872.140000] usb 1-1: new full speed USB device using uhci_hcd and address 5
Oct 10 16:31:43 localhost kernel: [17179882.660000] usb 1-1: new full speed USB device using uhci_hcd and address 6
Oct 10 16:35:19 localhost kernel: [17180098.628000] usb 1-1: new full speed USB device using uhci_hcd and address 7
Oct 10 16:35:19 localhost kernel: [17180098.772000] scsi1 : SCSI emulation for USB Mass Storage devices
Oct 10 16:35:24 localhost kernel: [17180103.776000]   Vendor: Generic   Model: USB Flash Disk    Rev: 0.00
Oct 10 16:35:24 localhost kernel: [17180103.776000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Oct 10 16:35:24 localhost kernel: [17180103.780000] SCSI device sda: 1013760 512-byte hdwr sectors (519 MB)
Oct 10 16:35:24 localhost kernel: [17180103.784000] sda: Write Protect is off
Oct 10 16:35:24 localhost kernel: [17180103.792000] sd 1:0:0:0: ioctl_internal_command return code = 8000002
Oct 10 16:35:24 localhost kernel: [17180103.792000]    : Current: sense key: No Sense
Oct 10 16:35:24 localhost kernel: [17180103.792000]     Additional sense: No additional sense information
Oct 10 16:35:24 localhost kernel: [17180103.796000] SCSI device sda: 1013760 512-byte hdwr sectors (519 MB)
Oct 10 16:35:24 localhost kernel: [17180103.800000] sda: Write Protect is off
Oct 10 16:35:24 localhost kernel: [17180103.800000]  sda: sda1
Oct 10 16:35:24 localhost kernel: [17180104.056000] sd 1:0:0:0: ioctl_internal_command return code = 8000002
Oct 10 16:35:24 localhost kernel: [17180104.056000]    : Current: sense key: No Sense
Oct 10 16:35:24 localhost kernel: [17180104.056000]     Additional sense: No additional sense information
Oct 10 16:35:24 localhost kernel: [17180104.056000] sd 1:0:0:0: Attached scsi removable disk sda
Oct 10 16:35:24 localhost kernel: [17180104.056000] sd 1:0:0:0: Attached scsi generic sg0 type 0
Oct 10 16:35:24 localhost kernel: [17180104.356000] sd 1:0:0:0: ioctl_internal_command return code = 8000002
Oct 10 16:35:24 localhost kernel: [17180104.360000]    : Current: sense key: No Sense
Oct 10 16:35:24 localhost kernel: [17180104.360000]     Additional sense: No additional sense information
Oct 10 16:35:39 localhost kernel: [17180118.800000] usb 1-1: USB disconnect, address 7
Oct 10 16:35:54 localhost kernel: [17180133.684000] usb 1-1: new full speed USB device using uhci_hcd and address 8
Oct 10 16:35:54 localhost kernel: [17180133.828000] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 10 16:35:59 localhost kernel: [17180138.832000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
Oct 10 16:35:59 localhost kernel: [17180138.832000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Oct 10 16:35:59 localhost kernel: [17180139.056000] SCSI device sda: 1000448 512-byte hdwr sectors (512 MB)
Oct 10 16:35:59 localhost kernel: [17180139.060000] sda: Write Protect is off
Oct 10 16:35:59 localhost kernel: [17180139.072000] SCSI device sda: 1000448 512-byte hdwr sectors (512 MB)
Oct 10 16:35:59 localhost kernel: [17180139.076000] sda: Write Protect is off
Oct 10 16:36:29 localhost kernel: [17180139.076000]  sda:<6>usb 1-1: reset full speed USB device using uhci_hcd and address 8Oct 10 16:36:48 localhost kernel: [17180187.732000] usb 1-1: reset full speed USB device using uhci_hcd and address 8
Oct 10 16:37:06 localhost kernel: [17180206.276000] usb 1-1: reset full speed USB device using uhci_hcd and address 8
Oct 10 16:37:17 localhost kernel: [17180216.796000] usb 1-1: reset full speed USB device using uhci_hcd and address 8
Oct 10 16:37:27 localhost kernel: [17180227.204000] usb 1-1: USB disconnect, address 8
Oct 10 16:37:27 localhost kernel: [17180227.204000] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery
Oct 10 16:37:27 localhost kernel: [17180227.204000] sd 2:0:0:0: SCSI error: return code = 0x50000
Oct 10 16:37:27 localhost kernel: [17180227.204000] end_request: I/O error, dev sda, sector 0
Oct 10 16:37:27 localhost kernel: [17180227.204000]  unable to read partition table
Oct 10 16:37:27 localhost kernel: [17180227.204000] sd 2:0:0:0: Attached scsi removable disk sda
Oct 10 16:37:27 localhost kernel: [17180227.204000] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 10 16:37:27 localhost kernel: [17180227.328000] usb 1-1: new full speed USB device using uhci_hcd and address 9
Oct 10 16:37:46 localhost kernel: [17180245.872000] usb 1-1: new full speed USB device using uhci_hcd and address 10
Oct 10 16:38:04 localhost kernel: [17180264.416000] usb 1-1: new full speed USB device using uhci_hcd and address 11
Oct 10 16:38:15 localhost kernel: [17180274.936000] usb 1-1: new full speed USB device using uhci_hcd and address 12

```

---

### Post by ashrack on 2006-10-26
anyone

---

### Post by ashrack on 2006-11-17
bump

---

### Post by scrooge_74 on 2006-11-17
I had that kind of troubles with kernel 2.4 back when using Debian stable, after upgrading i did not had that trouble anymore, and with Dapper I haven't had any troubles.

maybe this tutorial can be of some use to you. [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/15776-how-mount-usb-flash-drives-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/15776-how-mount-usb-flash-drives-linux.html)

Good luck

---

### Post by quadrispro on 2007-07-11
i have the same problem with an usb pendrive on Feisty Fawn (linux 2.6.20-16-generic)

**tail -f /var/log/messages**

```

Jul 11 16:32:59 quadrispro-desktop kernel: [  516.780441] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.788943] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.797441] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.805941] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.815139] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.823938] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.832435] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.840940] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.849442] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  516.857940] sr0: disc change detected.
Jul 11 16:32:59 quadrispro-desktop kernel: [  517.106478] sd 2:0:0:1: ioctl_internal_command return code = 8000002
Jul 11 16:32:59 quadrispro-desktop kernel: [  517.106482]    : Current: sense key: No Sense
Jul 11 16:32:59 quadrispro-desktop kernel: [  517.106484]     Additional sense: No additional sense information
Jul 11 16:33:00 quadrispro-desktop kernel: [  517.527422] sr0: disc change detected.
Jul 11 16:33:00 quadrispro-desktop kernel: [  517.536440] sr0: disc change detected.
Jul 11 16:33:00 quadrispro-desktop kernel: [  517.544944] sr0: disc change detected.
Jul 11 16:33:00 quadrispro-desktop kernel: [  517.553433] sr0: disc change detected.

```



**lsusb**

```

Bus 002 Device 002: ID 0ed1:7636 WinMaxGroup 

```



**cat /proc/bus/usb/devices**

```

T: Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=480 MxCh= 8
B: Alloc= 0/800 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 2.00 Cls=09(hub ) Sub=00 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-16-generic ehci_hcd
S: Product=EHCI Host Controller
S: SerialNumber=0000:00:0f.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 4 Ivl=256ms

T: Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=12 MxCh= 3
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-16-generic ohci_hcd
S: Product=OHCI Host Controller
S: SerialNumber=0000:00:0f.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms

T: Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=12 MxCh= 3
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-16-generic ohci_hcd
S: Product=OHCI Host Controller
S: SerialNumber=0000:00:0f.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms

T: Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=12 MxCh= 3
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-16-generic ohci_hcd
S: Product=OHCI Host Controller
S: SerialNumber=0000:00:0f.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms

T: Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 3 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs= 1
P: Vendor=03f0 ProdID=1604 Rev= 1.00
S: Manufacturer=Hewlett-Packard
S: Product=DeskJet 940C
S: SerialNumber=HU24Q1N16TCO
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr= 2mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E: Ad=81(I) Atr=02(Bulk) MxPS= 64 Ivl=0ms
E: Ad=02(O) Atr=02(Bulk) MxPS= 64 Ivl=0ms

T: Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#= 7 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0ed1 ProdID=7636 Rev=10.01
S: Manufacturer=TGE
S: Product=Digital MP3 Audio Player
S: SerialNumber=23DE8E2A95F5C80E
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E: Ad=81(I) Atr=02(Bulk) MxPS= 64 Ivl=0ms
E: Ad=02(O) Atr=02(Bulk) MxPS= 64 Ivl=0ms

```

---

### Post by quadrispro on 2007-12-07
I have the same problem with Gutsy.

Currently, a **_[bug is open in Launchpad](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125250)_**

---

### Post by victorgreen on 2007-12-07
What file system are these drives formatted in?

---

### Post by zero244 on 2007-12-07
This works for me

sudo rmmod ehci_hcd
Password:

After you type that in a terminal window......then plug in your usb drive.
This is for USB flash media.
I couldnt get any of my mp3 players to mount until I used this command.
Now they all work great.....they even run at USB 2.0 speed which they dont do in Windows XP.

---

### Post by quadrispro on 2007-12-07
> **victorgreen said:**
> What file system are these drives formatted in?

fat32


ok, these are my media:

[[IMG]http://img45.imageshack.us/img45/9149/screenshot1nj8.th.png[/IMG]](http://img45.imageshack.us/my.php?image=screenshot1nj8.png)

these are my media after inserting mp3 player

[[IMG]http://img89.imageshack.us/img89/9341/screenshot2eq5.th.png[/IMG]](http://img89.imageshack.us/my.php?image=screenshot2eq5.png)

and these are my media after I've tried to mount (right click -> mount) the USB device:

[[IMG]http://img479.imageshack.us/img479/870/screenshot3ui0.th.png[/IMG]](http://img479.imageshack.us/my.php?image=screenshot3ui0.png)

> **zero244 said:**
> This works for me

sudo rmmod ehci_hcd


It doesn't work...

---

