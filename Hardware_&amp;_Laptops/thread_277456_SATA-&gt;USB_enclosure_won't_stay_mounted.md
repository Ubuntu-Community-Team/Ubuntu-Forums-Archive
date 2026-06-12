---
title: "SATA-&gt;USB enclosure won't stay mounted"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by a212359 on 2006-10-14
edit: I ended up taking the enclosure back to the store, and they
confirmed that it was a physical problem with the device, gave me
a different one and it works fine.

---------------------------------
I have a laptop and a desktop running ubuntu. I have to get rid of the
desktop so I bought an enclosure (SATA->USB) for a 320GB (seagate) SATA
drive which was in the desktop, so I can continue using the drive (one partition, ext3). 
well, what I was hoping would be a 5 minute task has turned into an all-day one...

For some reason I can't get it to work properly when I plug it
in to my laptop.  I know there is no problem with the drive, since it works fine in the other machine.

What happens is that I plug in the USB and power on the drive. The drive
automounts, and then about 5 or 10 seconds later the USB connection just fails, and the automount point is gone.  
(btw, all my other USB devices (external IDE HDD,camera, usb stick drives) automount and function fine).

I tried all four usb ports, same behavior. I checked with an old
gParted live cd I had around, and the behavior is the same - I
can see the drive for a few seconds and then the usb connection
fails.  I guess that means its a kernel issue and not a specific
ubuntu one. Also tried switching out the USB cord, no luck.

I also read $rmmod ehci_hcd might help (to force a slower USB connection),
but it did not. I then updated to edgy, thinking that may help, but the
behavior is the same...

I have read about some similar problems but no solutions. Any ideas?

here is dmesg output from what happens.

[17179823.896000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[17179824.028000] usb 4-3: configuration #1 chosen from 1 choice
[17179824.204000] usbcore: registered new driver libusual
[17179824.248000] Initializing USB Mass Storage driver...
[17179824.248000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179824.248000] usb-storage: device found at 4
[17179824.248000] usb-storage: waiting for device to settle before scanning
[17179824.248000] usbcore: registered new driver usb-storage
[17179824.248000] USB Mass Storage support registered.
[17179829.336000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179829.336000] sda: Write Protect is off
[17179829.336000] sda: Mode Sense: 00 38 00 00
[17179829.336000] sda: assuming drive cache: write through
[17179829.336000]  sda: sda1
[17179829.352000] sd 0:0:0:0: Attached scsi disk sda
[17179829.364000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179829.700000] kjournald starting.  Commit interval 5 seconds
[17179829.712000] EXT3 FS on sda1, internal journal
[17179829.712000] EXT3-fs: mounted filesystem with ordered data mode.

and 5-10 seconds later:

[17179833.496000] usb 4-3: USB disconnect, address 4
[17179833.580000]  0:0:0:0: rejecting I/O to dead device
[17179833.580000] Buffer I/O error on device sda1, logical block 0
[17179833.580000] lost page write due to I/O error on sda1

here is the output from /proc/bus/usb/devices on the enclosure
(during the few seconds its working)

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=152d ProdID=2338 Rev= 1.00
S:  Manufacturer=JMicron
S:  Product=JM20338 SATA, USB Combo
S:  SerialNumber=222231F06738
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

big thanks for any help!

---

### Post by kidders on 2006-10-14
I'm sorry if this turns out to be a dumb idea, but (since you're talking about a laptop), is there something power-related going on? "usb 4-3: USB disconnect, address 4" is something you'd usually only see if you physically unplugged a device, so I can't help wondering if something is turning it off after a brief period of inactivity.

---

### Post by a212359 on 2006-10-15
If its a power problem I am not sure how to fix or even check it. The laptop is plugged in and the enclosure 
has a power supply which is also plugged in. 

As a kind of test I plugged in the drive and immediatly started mplayer to play an .avi file on the drive. 
It started playing without problem and died about 10 or so seconds in, here is how mplayer died:

A:  28.5 V:  28.4 A-V:  0.020 ct:  0.001 683/683 13%  0%  5.6% 0 0 
Message from syslogd@nb35949 at Sun Oct 15 22:43:30 2006 ...
nb35949 kernel: [17278313.996000] journal commit I/O error5.6% 0 0 
[mpeg4 @ 0x87dc78c]ac-tex damaged at 36 1989/689 13%  0%  5.6% 0 0 
[mpeg4 @ 0x87dc78c]Error at MB: 796
[mpeg4 @ 0x87dc78c]concealing 130 DC, 130 AC, 130 MV errors
A:  28.8 V:  28.7 A-V:  0.090 ct: -0.001 690/690 14%  0%  5.6% 0 0 
alsa-uninit: pcm closed
Exiting... (End of file)

If it still sounds like a power problem, any idea how to fix it? I'm 
really at a loss. If not a power problem, any idea what it may be?

Here is the dmesg output from the test above(a bit more info than my first post)
```

[17278263.616000] usb 2-1: new high speed USB device using ehci_hcd and address 
8
[17278263.752000] usb 2-1: configuration #1 chosen from 1 choice
[17278263.752000] scsi2 : SCSI emulation for USB Mass Storage devices
[17278263.752000] usb-storage: device found at 8
[17278263.752000] usb-storage: waiting for device to settle before scanning
[17278268.756000] usb-storage: device scan complete
[17278268.756000]   Vendor: ST332062  Model:         3QF06W38  Rev: D   
[17278268.756000]   Type:   Direct-Access                      ANSI SCSI revisio
n: 02
[17278268.760000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17278268.760000] sda: Write Protect is off
[17278268.760000] sda: Mode Sense: 00 38 00 00
[17278268.760000] sda: assuming drive cache: write through
[17278268.760000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17278268.760000] sda: Write Protect is off
[17278268.760000] sda: Mode Sense: 00 38 00 00[17278268.760000] sda: assuming drive cache: write through
[17278268.760000]  sda: sda1
[17278268.772000] sd 2:0:0:0: Attached scsi disk sda
[17278268.772000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17278269.400000] kjournald starting.  Commit interval 5 seconds
[17278269.412000] EXT3 FS on sda1, internal journal
[17278269.412000] EXT3-fs: recovery complete.
[17278269.412000] EXT3-fs: mounted filesystem with ordered data mode.
[17278313.996000] usb 2-1: USB disconnect, address 8
[17278313.996000] sd 2:0:0:0: SCSI error: return code = 0x10000
[17278313.996000] end_request: I/O error, dev sda, sector 67959223
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] sd 2:0:0:0: SCSI error: return code = 0x10000
[17278313.996000] end_request: I/O error, dev sda, sector 67959463
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] sd 2:0:0:0: SCSI error: return code = 0x10000
[17278313.996000] end_request: I/O error, dev sda, sector 67959463
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] Buffer I/O error on device sda1, logical block 565
[17278313.996000] lost page write due to I/O error on sda1
[17278313.996000] Aborting journal on device sda1.
[17278313.996000] journal commit I/O error
[17278313.996000] sd 2:0:0:0: rejecting I/O to device being removed
[17278313.996000] Buffer I/O error on device sda1, logical block 3342338
[17278313.996000] lost page write due to I/O error on sda1
[17278314.268000]  2:0:0:0: rejecting I/O to dead device
[17278314.268000]  2:0:0:0: rejecting I/O to dead device
[17278314.268000]  2:0:0:0: rejecting I/O to dead device
[17278314.268000]  2:0:0:0: rejecting I/O to dead device

```

---

### Post by kidders on 2006-10-19
Sorry I haven't replied sooner. I'm afraid anything I suggest would be a bit of a shot in the dark ... power saving isn't something I'm tremendously experienced with. It almost seems as if it's the only reasonable explanation though, since I'm at a loss to find anything else that would kill something that works perfectly, after a few moments of operation.

If it were me, I would try disabling automounting and powersaving. That way, most of the mysterious things that happen in the background, around the time you plug devices in would be off. First though, take a look at the man page for **hdparm**. I wonder if manually altering your drive's spin-down time could be the answer.

---

