---
title: "USB-Device not detected (SonyEricsson M600i)"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by achim.wessling on 2006-07-31
Hallo,

my handy, a SonyEricsson M600i, isn't detected on my **Dapper** installation. I've a **Debian Sarge** installation where it's working fine.

My *dmesg* after attaching the device to my **Dapper** looks as follows:

```

[17189057.624000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17189057.888000] scsi5 : SCSI emulation for USB Mass Storage devices
[17189057.888000] usb-storage: device found at 3
[17189057.888000] usb-storage: waiting for device to settle before scanning
[17189062.940000]   Vendor:           Model: M600i             Rev: 1.0
[17189062.940000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17189062.948000] SCSI device sdb: 121822 512-byte hdwr sectors (62 MB)
[17189062.952000] sdb: Write Protect is off
[17189062.952000] sdb: Mode Sense: 03 00 00 00
[17189062.952000] sdb: assuming drive cache: write through
[17189062.964000] SCSI device sdb: 121822 512-byte hdwr sectors (62 MB)
[17189062.968000] sdb: Write Protect is off
[17189062.968000] sdb: Mode Sense: 03 00 00 00
[17189062.968000] sdb: assuming drive cache: write through
[17189062.968000]  sdb:
[17189062.976000] sd 5:0:0:0: Attached scsi removable disk sdb
[17189062.976000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[17189062.976000] usb-storage: device scan complete
[17189063.412000] end_request: I/O error, dev sdb, sector 121816
[17189063.412000] printk: 252 messages suppressed.
[17189063.412000] Buffer I/O error on device sdb, logical block 60908
[17189063.412000] Buffer I/O error on device sdb, logical block 60909
[17189063.412000] Buffer I/O error on device sdb, logical block 60910
[17189063.420000] end_request: I/O error, dev sdb, sector 121816
[17189063.420000] Buffer I/O error on device sdb, logical block 60908
[17189063.420000] Buffer I/O error on device sdb, logical block 60909
[17189063.420000] Buffer I/O error on device sdb, logical block 60910
[17189063.432000] end_request: I/O error, dev sdb, sector 121816
[17189063.432000] Buffer I/O error on device sdb, logical block 60908
[17189063.432000] Buffer I/O error on device sdb, logical block 60909
[17189063.432000] Buffer I/O error on device sdb, logical block 60910
[17189063.440000] end_request: I/O error, dev sdb, sector 121816
[17189063.440000] Buffer I/O error on device sdb, logical block 60908
[17189063.448000] end_request: I/O error, dev sdb, sector 121816
[17189063.460000] end_request: I/O error, dev sdb, sector 121816
[17189063.468000] end_request: I/O error, dev sdb, sector 121752
[17189063.480000] end_request: I/O error, dev sdb, sector 121752
[17189063.488000] end_request: I/O error, dev sdb, sector 121808
[17189063.496000] end_request: I/O error, dev sdb, sector 121808
[17189063.508000] end_request: I/O error, dev sdb, sector 0
[17189063.516000] end_request: I/O error, dev sdb, sector 0
[17189063.528000] end_request: I/O error, dev sdb, sector 0
[17189063.572000] end_request: I/O error, dev sdb, sector 0
[17189063.584000] end_request: I/O error, dev sdb, sector 0
[17189063.592000] end_request: I/O error, dev sdb, sector 0
[17189063.600000] end_request: I/O error, dev sdb, sector 0
[17189063.612000] end_request: I/O error, dev sdb, sector 0
[17189063.716000] end_request: I/O error, dev sdb, sector 72
[17189063.724000] end_request: I/O error, dev sdb, sector 0
[17189063.736000] end_request: I/O error, dev sdb, sector 0
[17189063.744000] end_request: I/O error, dev sdb, sector 0
[17189063.752000] end_request: I/O error, dev sdb, sector 0
[17189063.764000] end_request: I/O error, dev sdb, sector 0
[17189063.772000] end_request: I/O error, dev sdb, sector 0
[17189063.784000] end_request: I/O error, dev sdb, sector 0
[17189063.792000] end_request: I/O error, dev sdb, sector 0
[17189063.804000] end_request: I/O error, dev sdb, sector 0
[17189063.812000] end_request: I/O error, dev sdb, sector 0
[17189063.824000] end_request: I/O error, dev sdb, sector 0
[17189063.832000] end_request: I/O error, dev sdb, sector 0
[17189063.840000] end_request: I/O error, dev sdb, sector 0
[17189063.852000] end_request: I/O error, dev sdb, sector 0
[17189063.860000] end_request: I/O error, dev sdb, sector 0
[17189063.872000] end_request: I/O error, dev sdb, sector 0
[17189063.880000] end_request: I/O error, dev sdb, sector 0
```

Under **Debian Sarge** it looks this way:

```

usb 1-1: new full speed USB device using address 5
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
  Vendor:           Model: M600i             Rev: 1.0
  Type:   Direct-Access                      ANSI SCSI revision: 02
USB Mass Storage device found at 5
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
SCSI device sda: 121822 512-byte hdwr sectors (62 MB)
sda: assuming Write Enabled
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0:
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
```

I checked the modules on both systems with *lsmod|grep usb*. When the device isn't attached both systems say:

```

usbhid                 32224  0
usbcore               119044  5 usbhid,ehci_hcd,uhci_hcd
```

With a small difference in the module size.

When the device is attached, I get under **Sarge**:

```

usb_storage            69056  0
usbhid                 32224  0
usbcore               119044  6 usb_storage,usbhid,ehci_hcd,uhci_hcd
scsi_mod              125228  4 sd_mod,usb_storage,sr_mod,sbp2
ide_core              139940  5 usb_storage,ide_cd,ide_generic,ide_disk,via82cxxx
```

Under **Dapper** it looks this way:

```

usb_storage            79488  0
usbhid                 42752  0
usbcore               139076  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
scsi_mod              145960  7 usb_storage,sr_mod,sbp2,sg,sd_mod,ahci,libata
```

So, where is my problem? What can I do to get the device work with **Dapper?**

---

### Post by chomski on 2006-08-09
<Bump!>
I'm in the same boat, just got the phone today. Can anyone shine some light on this?

---

### Post by achim.wessling on 2006-08-10
I tried to reformat the device with the phone, with Windows and with Debian. But after doing so, I was never able to connect to Dapper. With Debian I made a new partition and I could use it with Debian afterwards, but not with Dapper? So I think, here is something really bad going on.

---

### Post by joh on 2006-08-17
```
[17193255.848000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[17193256.028000] usb 3-1: configuration #1 chosen from 1 choice
[17193256.032000] cdc_acm 3-1:1.1: ttyACM0: USB ACM device
[17193256.040000] cdc_acm 3-1:1.3: ttyACM1: USB ACM device
[17193256.044000] cdc_acm 3-1:1.5: ttyACM2: USB ACM device

```


Thats the only output I get i dmesg, runing Edgy Edge. I'm not even able to format it.

---

### Post by achim.wessling on 2006-08-17
I get more and more the impression, that we will get no help here. I figured around in the mean time a little bit, but didn't solve the probleme.

Do we have any chance to get anywhere else help? :frown:

---

### Post by joh on 2006-08-17
Sorry for my last post. I hadn't turned on USB file transfer (mass storage) on my phone.

[http://lists-archives.org/linux-usb-users/02832-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html](http://lists-archives.org/linux-usb-users/02832-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html)

Seems like Nokia N70 users has the same problem. According to the mail thread the Nokia device reports that it has more space than it acctualy has, and Linux doesn't really like that.

The thread has a patch, but it seems to be Nokia specific.

Which kernel did you use on the Debian system where you mounted the drive?

---

### Post by rck_hitokiri on 2006-08-18
just need to do more research, im having the same prob too. please post if you have a solution. thanks :)

---

### Post by achim.wessling on 2006-08-18
Did someone tried the kernelfix for the Nokia mentioned above with the SonyEricsson M600i. I'm not willing to build my own kernel, because I never did so8-[ . Can I test this fix without building a kernel?

---

### Post by nberelidze on 2006-09-27
here you can find patch for m600i. Not tested yet. Will post follow up if I have success.

[http://www.uwsg.iu.edu/hypermail/linux/kernel/0608.3/1540.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0608.3/1540.html)

---

### Post by nberelidze on 2006-09-28
Good news! It works - the phone must be in USB "File Transfer" mode.

---

### Post by ingo on 2006-12-15
yeah, i got it working as a usb device after having switched on the "file transfer" mode. 

downloaded kmobiletools as well to do stuff with phonebooks etc. but no joy. has anybody managed to tinker with mobile gnome or kde add-ons and got their's working?

---

### Post by Vitus on 2007-10-14
Anything new to this?

I juest got my s-e M600i and it is detected when in file transfer mode (otherwise it's not).  But transfer speed is really, really slow (unusable).  When I look at it in the USB device monitor the USB speed changes back and forth between 12Mbps (full speed) and 480Mbps (2.0, high speed), so there is a lowlevel USB problem with that device.

M600i  FW R6A16
Dapper Drake 2.6.15-29-686 #1 SMP PREEMPT

dmesg shows lots of this:

sd 0:0:0:0: SCSI error: return code = 0x10070000
[17184829.432000] end_request: I/O error, dev sda, sector 1743
[17184829.432000] Buffer I/O error on device sda, logical block 1743
[17184829.432000] lost page write due to I/O error on sda

---

