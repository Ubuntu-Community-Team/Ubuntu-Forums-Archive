---
title: "usb memory stick...SLOW..."
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by dbrine on 2005-08-20
My memory stick is really slow in linux but fast in windows????

---

### Post by jasmuz on 2005-08-20
USB stick speeds are only related to the USB version 1 or 2, whereas 2.0 allows for faster data transfers, i use a USB pendrive, and speed on both Windows Xp and Ubuntu are the same.

---

### Post by MattVogt on 2005-08-20
Actually, I get this problem also - I have a USB 2 stick, but my system has only USB1.1 ports.

Dual-booting between windows xp and hoary, usb tranfers on windows are roughly 2-3 times as quick as the same transfers on linux.

If I'm copying over 50 MB or so, it's quicker to boot back into windows to do the transfer...

---

### Post by GeirG on 2005-08-28
I do experience this too.
Haven't had the time to dig into what causes this though.
I would say the speed difference is considrably more than 2-3 times, but I haven't done any serious testing and compared the numbers.
 
Regards

---

### Post by Oxygene on 2005-08-30
[QUOTE=GeirG]I do experience this too.
Haven't had the time to dig into what causes this though.
I would say the speed difference is considrably more than 2-3 times, but I haven't done any serious testing and compared the numbers.
 
Regards[/QUOTE]
 I have this problem too. It already worked at high speed once some days ago but now it is very slow. The only thing I did was adding some backports to hoary.

What can be done about it? My stick would provide 15MB/s writing speed but it needs several minutes to copy 100 MB

---

### Post by sepeto on 2005-08-30
[QUOTE=dbrine]My memory stick is really slow in linux but fast in windows????[/QUOTE]

I had that same problem from time ago.
I was because of usb-modules was loading in wrong order.
To use usb 2.0 devices you have to load usb 2.0 modules first.

Last time when I was using hotplug to load modules, it loaded usb 1.0 modules first, so all devices was in usb 1.0 state.

Usb 2.0 module is ehcd-hcd
and 1.0 module is uhci-hcd on common hardwares.

Do lsmod to see what modules you are using. If you using same modules, try this
---- add /etc/modules -----
[B]#usb modules
ehcd-hcd
uhci-hcd[/B]
-----------------------------------

---

### Post by GeirG on 2005-08-30
Good idea, but it seems to be something else in my case :-(

Dmesg reports the following action :

```
usb 5-1: new high speed USB device using ehci_hcd and address 12
hub 5-1:1.0: USB hub found
hub 5-1:1.0: 1 port detected
usb 5-1.1: new high speed USB device using ehci_hcd and address 13
scsi8 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 13
usb-storage: waiting for device to settle before scanning
  Vendor: Corsair   Model: Flash Voyager     Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdd: 4063232 512-byte hdwr sectors (2080 MB)
sdd: Write Protect is off
sdd: Mode Sense: 00 26 00 00
sdd: assuming drive cache: write through
SCSI device sdd: 4063232 512-byte hdwr sectors (2080 MB)
sdd: Write Protect is off
sdd: Mode Sense: 00 26 00 00
sdd: assuming drive cache: write through
 /dev/scsi/host8/bus0/target0/lun0: p1
Attached scsi removable disk sdd at scsi8, channel 0, id 0, lun 0
usb-storage: device scan complete
```

Seems to recognise it correctly.
Also, I can read from it with acceptable speed, but the writing is nowhere near the performance in Windows. Right now I'm writing at about 5Mb per sec.

Regards,

---

### Post by Oxygene on 2005-08-30
Hehe, you encounter EXACTLY the same problem (the only difference is that your stick is four time as big as mine.... the USB one, I mean!)

Reading seems to be faster, although not 100%. I measured ca. 12 MB/s compared to about 20MB/s the stick should serve.

```

Aug 30 21:03:10 localhost kernel: usb 4-1: new high speed USB device using ehci_hcd and address 5
Aug 30 21:03:10 localhost kernel: hub 4-1:1.0: USB hub found
Aug 30 21:03:10 localhost kernel: hub 4-1:1.0: 1 port detected
Aug 30 21:03:10 localhost usb.agent[16781]:      usbcore: already loaded
Aug 30 21:03:11 localhost kernel: usb 4-1.1: new high speed USB device using ehci_hcd and address 6
Aug 30 21:03:11 localhost kernel: scsi7 : SCSI emulation for USB Mass Storage devices
Aug 30 21:03:11 localhost kernel: usb-storage: device found at 6
Aug 30 21:03:11 localhost kernel: usb-storage: waiting for device to settle before scanning
Aug 30 21:03:11 localhost usb.agent[16835]:      usb-storage: already loaded
Aug 30 21:03:15 localhost ntpd[8345]: sendto(2001:660:5001:100::6): Network is unreachable
Aug 30 21:03:16 localhost kernel:   Vendor: Corsair   Model: Flash Voyager     Rev: 1.00
Aug 30 21:03:16 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Aug 30 21:03:16 localhost kernel: SCSI device sda: 1015808 512-byte hdwr sectors (520 MB)
Aug 30 21:03:16 localhost kernel: sda: Write Protect is off
Aug 30 21:03:16 localhost kernel: sda: Mode Sense: 00 26 00 00
Aug 30 21:03:16 localhost kernel: sda: assuming drive cache: write through
Aug 30 21:03:16 localhost kernel: SCSI device sda: 1015808 512-byte hdwr sectors (520 MB)
Aug 30 21:03:16 localhost kernel: sda: Write Protect is off
Aug 30 21:03:16 localhost kernel: sda: Mode Sense: 00 26 00 00
Aug 30 21:03:16 localhost kernel: sda: assuming drive cache: write through
Aug 30 21:03:16 localhost kernel:  /dev/scsi/host7/bus0/target0/lun0: p1
Aug 30 21:03:16 localhost kernel: Attached scsi removable disk sda at scsi7, channel 0, id 0, lun 0
Aug 30 21:03:16 localhost kernel: usb-storage: device scan complete
```


/proc/bus/usb/devices gives

```
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=067b ProdID=2515 Rev= 1.00
S:  Manufacturer=Prolific Technology Inc.
S:  Product=USB Embedded Hub
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms
```

Any help appreciated. Thanks in advance.

---

### Post by i_netguru on 2005-09-05
Hi
I 2 have a usb pendrive problem. It is not accessed in linus. Yah may be it is not mounting it since no entry is available. But where 2 keep what entries so that memory stick can be accessed in Ubuntu?

---

### Post by mlomker on 2005-09-05
Netguru, insert your USB after booting and then type **dmesg** to see what it is being installed as.

I have the same problem with pendrive speed--it's painfully slow but works.  My drive is an old 1.0, so I know this isn't a 2.0 module conflict of some kind.  I also have all those modules built into a custom kernel, so...

---

### Post by cheezx on 2005-09-05
well my situation is pretty weird:

I have a Dell Inspiron 6000 and a Lexar Jumpdrive.  The transfer speed is fast (~7.7MB/s) but the recognition of the drive is very slow.  I insert the drive and this is the DMESG:

```
sdb: Mode Sense: 43 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 2026592 512-byte hdwr sectors (1038 MB)
sdb: Write Protect is off
sdb: Mode Sense: 43 00 00 00
sdb: assuming drive cache: write through
 /dev/scsi/host6/bus0/target0/lun0: p1
Attached scsi removable disk sdb at scsi6, channel 0, id 0, lun 0
Attached scsi generic sg2 at scsi6, channel 0, id 0, lun 0,  type 0
usb-storage: device scan complete
```

when I try to mount it with *mount /dev/sdb foo* , it does not find the sdb device.  After a good 5min, it finally does.  This is pretty slow to "initialize" the sdb device.  Any ideas?

---

### Post by i_netguru on 2005-09-06
Hi
thanks. I will try & comeback. :roll:

---

### Post by vik4 on 2005-09-28
I've got a similar issue with my iRiver H300 USB external harddrive. The device is usb2, though the computer only has usb1. Nonetheless, browsing files is painfully slow in gnome, considerably slower than in windows or even a linux commandline. Clicking on a directory takes a good 10-30 seconds to display the contents, while in windows it is virtually instant.

data transfers are the same speed in win and lin. 

any ideas?

---

