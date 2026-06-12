---
title: "USB Hard Drive too slow?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by mgchan on 2006-03-25
I recently put a 300 GB hard drive into a USB 2.0 enclosure and connected it to my machine.  However, it seems to be running painfully slow.  I did a 'time cp data1.cab /tmp/' on a 25 MB data1.cab file (from the USB drive) and it took 24 seconds.

How can I check if 1) my device is connected properly at USB 2.0 speed and 2) there are any problems with the connections otherwise?

Here is the /var/log/messages text after connecting the drive:
```
Mar 25 04:11:41 ubuntu kernel: usb 1-2: new full speed USB device using uhci_hcd and address 3
Mar 25 04:11:41 ubuntu kernel: scsi3 : SCSI emulation for USB Mass Storage devices
Mar 25 04:11:42 ubuntu usb.agent[11996]:      usb-storage: already loaded
Mar 25 04:11:46 ubuntu kernel:   Vendor: ST330063  Model: 1A                Rev: 0000
Mar 25 04:11:46 ubuntu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar 25 04:11:46 ubuntu kernel: SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
Mar 25 04:11:46 ubuntu kernel: SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
Mar 25 04:11:46 ubuntu kernel:  sda: sda1
Mar 25 04:11:46 ubuntu kernel: Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
Mar 25 04:11:46 ubuntu kernel: Attached scsi generic sg0 at scsi3, channel 0, id 0, lun 0,  type 0
Mar 25 04:11:47 ubuntu scsi.agent[12038]: disk at /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2:1.0/host3/target3:0:0/3:0:0:0
Mar 25 04:12:07 ubuntu kernel: kjournald starting.  Commit interval 5 seconds
Mar 25 04:12:07 ubuntu kernel: EXT3 FS on sda1, internal journal
Mar 25 04:12:07 ubuntu kernel: EXT3-fs: mounted filesystem with ordered data mode.

```

And here is the output from lsusb:
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 002: ID 0471:0815 Philips
Bus 001 Device 001: ID 0000:0000

```

The Philips device is a remote control which seems to be working properly.

Here is the output from hdparm:
```
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   788 MB in  2.00 seconds = 393.19 MB/sec
 Timing buffered disk reads:    4 MB in  4.12 seconds = 994.11 kB/sec

```

By contrast, my regular IDE has a slightly higher cached read but a vastly higher (30 MB/sec) buffered disk read.

---

### Post by alm on 2006-03-26
[QUOTE=mgchan]I recently put a 300 GB hard drive into a USB 2.0 enclosure and connected it to my machine.  However, it seems to be running painfully slow.  I did a 'time cp data1.cab /tmp/' on a 25 MB data1.cab file (from the USB drive) and it took 24 seconds.

How can I check if 1) my device is connected properly at USB 2.0 speed and 2) there are any problems with the connections otherwise?

Here is the /var/log/messages text after connecting the drive:
```
Mar 25 04:11:41 ubuntu kernel: usb 1-2: new full speed USB device using uhci_hcd and address 3
Mar 25 04:11:41 ubuntu kernel: scsi3 : SCSI emulation for USB Mass Storage devices
Mar 25 04:11:42 ubuntu usb.agent [11996]:      usb-storage: already loaded
Mar 25 04:11:46 ubuntu kernel:   Vendor: ST330063  Model: 1A                Rev: 0000
Mar 25 04:11:46 ubuntu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar 25 04:11:46 ubuntu kernel: SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
Mar 25 04:11:46 ubuntu kernel: SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
Mar 25 04:11:46 ubuntu kernel:  sda: sda1
Mar 25 04:11:46 ubuntu kernel: Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
Mar 25 04:11:46 ubuntu kernel: Attached scsi generic sg0 at scsi3, channel 0, id 0, lun 0,  type 0
Mar 25 04:11:47 ubuntu scsi.agent [12038]: disk at /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2:1.0/host3/target3:0:0/3:0:0:0
Mar 25 04:12:07 ubuntu kernel: kjournald starting.  Commit interval 5 seconds
Mar 25 04:12:07 ubuntu kernel: EXT3 FS on sda1, internal journal
Mar 25 04:12:07 ubuntu kernel: EXT3-fs: mounted filesystem with ordered data mode.

```

And here is the output from lsusb:
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 002: ID 0471:0815 Philips
Bus 001 Device 001: ID 0000:0000

```

The Philips device is a remote control which seems to be working properly.

Here is the output from hdparm:
```
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   788 MB in  2.00 seconds = 393.19 MB/sec
 Timing buffered disk reads:    4 MB in  4.12 seconds = 994.11 kB/sec

```

By contrast, my regular IDE has a slightly higher cached read but a vastly higher (30 MB/sec) buffered disk read.[/QUOTE]


Hi mgchan, sorry to say that I have the same disgusting problem. Perhaps it helps to say that I think it may be a USB 1.1 Vs USB 2.0 problem because when I type "cat /proc/bus/usb/devices" I get:

    T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 [COLOR="Red"]Spd=12[/COLOR]  MxCh= 0
    D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
    P:  Vendor=059f ProdID=0651 Rev= 0.00
    S:  Manufacturer=LaCie
    S:  Product=LaCie Hard Drive USB
    S:  SerialNumber=10000E000B0EA187
    C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
    I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
    E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
    E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

And I have read at linux-usb org that instead 12 Mbits/sec speed it should report 480 Mbits/sec

As a proper newbie ](*,) , any help will be deeply appreciated.

---

### Post by anindya_m on 2006-04-28
I have the same problem on my Inspiron 9300 and also some desktops running on Breezy. The funny thing is dmesg shows it as a "high speed device" and the entry in /proc/bus/usb/devices corresponding to my drive shows 480 Mbps, but it is still painfully slow. This is also the case with the Fedora systems I have. On Windows on the same machine (Inspiron) it works at full speed.

Any help will be appreciated.

---

### Post by nvbauer on 2006-05-28
Bump - I'm using Dapper and have the same problem. 

T:  Bus=05 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0d49 ProdID=7110 Rev= 2.03
S:  Manufacturer=Maxtor
S:  Product=OneTouch II
S:  SerialNumber=L20X9L8G
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=32ms

---

### Post by billybofh on 2006-06-08
I have much the same problem since upgrading to Dapper.  USB devices either take forever or run _extremely_ slowly.  All of them are showing up as 12mb speed-wise even though they were happily running at the full 480 usb2.0 in Breezy.

I posted another thread [here]("http://ubuntuforums.org/showthread.php?t=188222").

---

### Post by gordonl on 2006-06-14
Same problem here. I did a clean install of dapper over breezy. My external hard drive performance then took a nose dive. The bus is listed as full speed (480Mbps), but i'm still getting less than 1MBps. This has happened to me with an AMD desktop and an AMD64 notebook both with VIA chipsets. It was worse before i removed ehci_hcd, i was getting <100KBps.

---

### Post by billybofh on 2006-06-14
I've managed to solve the problem - kind of....

If I rmmod ehci_hcd, plug in my usb device, umount it, then modprobe ehci_hcd and plug in the device again I get full speed usb 2.0.

Not exactly satisfactory, but it works for the moment....

---

### Post by Ollan on 2006-09-14
I have same problem since I did a clean installation of Dapper.

---

### Post by x64Jimbo on 2006-09-18
Bump!
What the heck. This seems like a pretty common issue. 
My system is an MSI mobo with ATI chipsets, Athlon64. 
Any external hard disk will actually start copying at USB2 speed, but after about 100MB or so it drops down to about 700KB/s. Even the iPod has the same problem. Anyone know of a bug report on this issue?

---

### Post by ewiget on 2006-10-01
same problem here too, dapper with full upgrades + latest kernel.  Here is some information:

```
T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1058 ProdID=0901 Rev= 2.06
S:  Manufacturer=Western Digital
S:  Product=External HDD
S:  SerialNumber=57442D5743414E4B34373539313636
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
```

uname -a:
```
2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux
```

root@server:~# lsmod | grep usb
```
usb_storage            82240  3
usblp                  16128  0
usbcore               147132  5 usb_storage,usblp,ehci_hcd,ohci_hcd
scsi_mod              160504  6 sg,sd_mod,sr_mod,sbp2,usb_storage,libata

```

I am curious to know, cause I was thinking about something....are usb2 devices the only usb devices plugged into the same hub/buss?  For example, I wonder if the speed restriction is maybe due to usb1 spec devices plugged into the same hub/buss rated at usb2?  For example, I show this with lsusb:

root@server:~# lsusb
```
Bus 002 Device 003: ID 1058:0901 Western Digital Technologies, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 001 Device 003: ID 0aec:5010 Neodio Technologies Corp. ND5010 Card Reader
Bus 001 Device 001: ID 0000:0000
```

Two of these are plugged into the back of the motherboard (I have 4 usb plugs on the back).  The Printer is rated usb1 and the western digital hard drive is usb2 - they are plugged in side by side.  The card reader is plugged into the front usb buss connector and it is rated usb1.  This is an Abit NV8 AMD64 motherboard and all front and rear usb connectors are usb2.0 spec.

If I think about it,  Iwill attempt to remove all the usb1 stuff and see if it makes a difference

Edited to include:  I did some research....and this is what I found from this thread:
[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg46546.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg46546.html)

**Usb2 specs 480Mb/s is really only 60MB/s**  (notice the difference)

Have a look, it also shows a test you can use to get a real speed.

---

### Post by x64Jimbo on 2006-10-02
I was aware that USB2 spec only allowed for 60MB/s but I'm not even getting 1MB/s. I'd be very happy if I could get half of the spec speed.

---

### Post by onyxrev on 2006-11-24
I had the same problem of full speed devices being reported as 12 Mb/s.

My USB hub switched to using ohci_hcd instead of ehci_hcd for some reason...

Blacklisting ohci_hcd in /etc/default/linux-restricted-modules-common didn't seem to make a difference, so I just renamed the kernel object like so...

sudo mv /lib/modules/2.6.17-10-generic/kernel/drivers/usb/host/ohci-hcd.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/host/ohci-hcd.bak

and then added the high speed modules to /etc/modules in the proper order:

ehci_hcd
uhci_hcd

rebooted and it's running at full speed again

---

### Post by lilalinux on 2007-06-22
If your hdd is detected as high speed device (480) and you can read fast but writing is slow, your hdd is most probably mounted with "sync" option enabled.
This might happen, if you mount via your windowmanager and hal.
You can configure this in many ways, and you might want to have a look at /etc/hal/fdi/policy/preferences.fdi and uncomment the section:

```
<!--
  The following shows how to put sync and noatime on for devices smaller then
  1Gb and off for device larger then that. Note that the sync option can wear
  out device faster then you'd like too. See
  http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html for
  more info.
-->
<!--
  <device>
...

```

---

### Post by ComradeVVA on 2007-09-29
Seems like every time you try to do something that doesn't involve apt-get, it turns into a research project in computer programming. My Vista box was doing 20 MB/s (without me having to do **anything**), but my Ubuntu starts out at 20 and then goes down to 700 KB/s. I've removed the comments around the code as suggested by lilalinux; seems to cause no change. However, I have not tried to do what onyxrev said simply b/c I'm a little uneasy about changing modules. Is there a more detailed tutorial to do that? 

I've read a lot about this recently, but there seems to be no easy solution. As a newbie, I'm running out resources.

Thanks,
ComradeVVA

---

### Post by ComradeVVA on 2007-09-29
I've removed the old module now, and my USB hard drive still does exactly the same thing. Anybody out there that knows any other ways of dealing with this problem?

---

### Post by dutchcow on 2007-10-11
Having the same issues here with several usb2 drives, all being detectd properly, my info's:

/proc/bus/usb/devices
```

01 Prnt=01 Port=05 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=13fd ProdID=1650 Rev= 4.36
S:  Manufacturer=Initio  
S:  Product=ST3320620AS     
S:  SerialNumber=0010101650000000W
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
```dmesg
```

[  556.078931] usb 2-6: new high speed USB device using ehci_hcd and address 4
[  556.145564] usb 2-6: configuration #1 chosen from 1 choice
[  556.145753] scsi3 : SCSI emulation for USB Mass Storage devices
[  556.145902] usb-storage: device found at 4
[  556.145906] usb-storage: waiting for device to settle before scanning
[  558.965262] usb-storage: device scan complete
[  558.966065] scsi 3:0:0:0: Direct-Access     Initio   ST3320620AS      4.36 PQ: 0 ANSI: 0
[  558.967935] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  558.969234] sd 3:0:0:0: [sdb] Write Protect is off
[  558.969240] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  558.969244] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  558.970795] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  558.972234] sd 3:0:0:0: [sdb] Write Protect is off
[  558.972239] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  558.972242] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  558.972246]  sdb: sdb1
[  558.979768] sd 3:0:0:0: [sdb] Attached SCSI disk
[  558.979825] sd 3:0:0:0: Attached scsi generic sg1 type 0
```hdparm
```

 Timing cached reads:   1690 MB in  2.00 seconds = 845.35 MB/sec
 Timing buffered disk reads:   58 MB in  3.11 seconds =  18.64 MB/sec
```I've also tried mounting it with and without syn, it doesnt make it go any faster or slower. Copying files takes ages and speed decreases while its copying, the drives work fine (full speed) on another pc with xp/vista.

---

### Post by Wydarr on 2008-01-31
I'm having the same problem. Plugged in an Iomega 250 GB HDD, and copying takes forever (The transfer rate is in the range of 4 Mbytes/sec). It seems to me that it's doing some kind of interval training. The SATA drive i'm copying from runs full speed for a couple of seconds, then it stops, and then, the cycle is repetead. I'm finding this to be a really annoying issue since I need to back-up almost 200 GB of data... which could take me close to 14 hours. Anybody can give a definitive solution? :confused:

P.S. O.S. Ubuntu 7.10 Gutsy Gibbon, kernel version 2.6.22-14-generic.

---

### Post by iGeorgie on 2008-03-17
I have this problem on Ubuntu Server, **not** on Ubuntu Desktop.

When I make a backup (approx. 250 Gb,) it takes a couple of hours on Desktop (not know exactly how much). But with the same amount of Gigs on Server it takes a few days! (70 hours to be exact).

I checked with the commands from this post (dmesg etc.) to see if the drive is detected right; and it is.

I will look over the Internet to find a solution... If I find it, I'll post it (don't count on it, I'm a rookie on Linux).

EDIT:
I solved the problem. I upgraded my server to 8.04. I functions great!

---

### Post by s2welee on 2008-04-11
Slow usb read times here as well.  Interestingly when I browse to the drive over the network, it is quick.  When I try to open a picture from the usb drive directly from 7.10 it takes almost a minute.  We are not talking gigantic pictures, these are from a 3.2mp camera.  Not sure what the problem is, but I thought I would throw one more into this possible bug.

---

