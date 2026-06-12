---
title: "SD cards stopped working under Breezy"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by abovett on 2005-12-30
I have two SD cards (256 MB and 512 MB) which I use in a camera (Samsung Digimax 202) and a USB card reader (made by PNY). Until recently I've had no problems, but the other day I plugged the PNY card reader with an SD card in it into a Breezy box and it refused to mount the device. Tried the other card - the same. They also fail to work on any other Breezy box (I've tried five) - BUT - they work fine under Windows XP and under Mandriva Linux 2006. They also work fine with the Hoary Live CD, but _not_ with the Breezy Live CD.

I'm 99% certain that they were working under Breezy (I've been running it more or less since it came out and I use the card reader regularly), so it _appears_ that something has happened to the cards. At first I thought a Ubuntu update had broken it but the test with the Breezy live CD indicates that's unlikely.

Looking at the dmesg output under Breezy shows that an I/O error is being reported. The full output is rather long (125 lines - I'll post it if required) but here's an extract:
```

[4298800.369000] usb 4-3.3: new high speed USB device using ehci_hcd and address 5
[4298800.414000] scsi2 : SCSI emulation for USB Mass Storage devices
[4298800.416000] usb-storage: device found at 5
[4298800.416000] usb-storage: waiting for device to settle before scanning
[4298805.416000]   Vendor: USB       Model: Storage Device    Rev:     
[4298805.416000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4298805.588000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[4298805.589000] sda: Write Protect is off
[4298805.589000] sda: Mode Sense: 03 00 00 00
[4298805.589000] sda: assuming drive cache: write through
[4298805.594000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[4298805.595000] sda: Write Protect is off
[4298805.595000] sda: Mode Sense: 03 00 00 00
[4298805.595000] sda: assuming drive cache: write through
[4298805.595000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4298805.599000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[4298805.602000] usb-storage: device scan complete
[4298806.766000] end_request: I/O error, dev sda, sector 498173
[4298806.766000] printk: 123 messages suppressed.
[4298806.766000] Buffer I/O error on device sda1, logical block 498072
[4298806.766000] Buffer I/O error on device sda1, logical block 498073

```

I also tried putting the cards in the camera and plugging the camera in via the USB port. This gives an even stranger problem. When it is initially plugged in, it recognises the camera ("Samsung Digimax 202" appears in the Places -> Computer window) but fails to mount it. The dmesg output in this case is similar to that above:

```

[4294806.002000] usb 4-3.3: new full speed USB device using ehci_hcd and address 3
[4294806.332000] SCSI subsystem initialized
[4294806.349000] Initializing USB Mass Storage driver...
[4294806.358000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294806.361000] usb-storage: device found at 3
[4294806.361000] usb-storage: waiting for device to settle before scanning
[4294806.363000] usbcore: registered new driver usb-storage
[4294806.363000] USB Mass Storage support registered.
[4294811.363000]   Vendor: Samsung   Model: Digimax 202       Rev: 1.00
[4294811.363000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294811.373000] usb-storage: device scan complete
[4294811.487000] SCSI device sda: 999424 512-byte hdwr sectors (512 MB)
[4294811.491000] sda: test WP failed, assume Write Enabled
[4294811.491000] sda: assuming drive cache: write through
[4294811.502000] SCSI device sda: 999424 512-byte hdwr sectors (512 MB)
[4294811.506000] sda: test WP failed, assume Write Enabled
[4294811.506000] sda: assuming drive cache: write through
[4294811.506000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4294811.526000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294811.964000] Buffer I/O error on device sda1, logical block 1000064
[4294811.964000] Buffer I/O error on device sda1, logical block 1000065
[4294811.964000] Buffer I/O error on device sda1, logical block 1000066
[4294811.964000] Buffer I/O error on device sda1, logical block 1000067
[4294811.964000] Buffer I/O error on device sda1, logical block 1000068
[4294811.964000] Buffer I/O error on device sda1, logical block 1000069
[4294811.964000] Buffer I/O error on device sda1, logical block 1000070
[4294811.964000] Buffer I/O error on device sda1, logical block 1000071
[4294811.966000] Buffer I/O error on device sda1, logical block 1000064
[4294811.966000] Buffer I/O error on device sda1, logical block 1000065

```

If I then click on the camera icon it mounts successfuly. Here's the dmesg output when that happens (carrying on from above):

```

[4294878.937000] UDF-fs: No partition found (1)
[4294879.150000] UDF-fs: No partition found (1)
[4294879.701000] Unable to identify CD-ROM format.
[4294880.185000] Unable to identify CD-ROM format.
[4294880.201000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

Does anyone have any idea what's going on here? Why should my cards stop working in the card reader? And why should they work on the 2nd attempt in the camera but not the first?

Hope someone can help

Andy B.

---

### Post by abovett on 2005-12-30
Update:

I've tried some other USB Flash drives and a removeable USB hard disk on my Breezy boxes - just to make sure - and they all work fine. So the problem is just with the SD cards.

Andy B.

---

### Post by abovett on 2005-12-31
If no-one knows the answer to this problem, can I ask: is anyone else using SD cards with Ubuntu - specifically with Breezy? If so, what size and type, and what sort of reader or camera? And are you having any problems?

This is quite important to me - I'm going to do a bit more research on the problem, and I'll raise it on Bugzilla if I can't find it there (haven't so far) but I'd like some additional input from other SD card users to know how general the problem is.

Andy B

---

### Post by abovett on 2005-12-31
Update:

Just tried plugging the USB SD card reader into a box running the Dapper Flight 2 live CD. I get the same behaviour as when plugging the camera in to Breezy (see above) - that is, it fails to mount and there are some errors in the dmesg output when it's first plugged in, but clicking on the icon in the "Computer" window in Nautilus mounts it.

Here's the dmesg output when it's first plugged in:

```

[17179776.332000] usb 1-3.3: new high speed USB device using ehci_hcd and addres s 3
[17179776.728000] SCSI subsystem initialized
[17179776.956000] Initializing USB Mass Storage driver...
[17179776.956000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179776.960000] usb-storage: device found at 3
[17179776.960000] usb-storage: waiting for device to settle before scanning
[17179776.960000] usbcore: registered new driver usb-storage
[17179776.960000] USB Mass Storage support registered.
[17179781.960000]   Vendor: USB       Model: Storage Device    Rev:
[17179781.960000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17179781.976000] usb-storage: device scan complete
[17179782.188000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[17179782.188000] sda: Write Protect is off
[17179782.188000] sda: Mode Sense: 03 00 00 00
[17179782.188000] sda: assuming drive cache: write through
[17179782.196000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[17179782.196000] sda: Write Protect is off
[17179782.196000] sda: Mode Sense: 03 00 00 00
[17179782.196000] sda: assuming drive cache: write through
[17179782.196000]  sda: sda1
[17179782.200000] sd 0:0:0:0: Attached scsi removable disk sda
[17179783.144000] end_request: I/O error, dev sda, sector 498173
[17179783.144000] Buffer I/O error on device sda1, logical block 498072
[17179783.144000] Buffer I/O error on device sda1, logical block 498073
[17179783.144000] Buffer I/O error on device sda1, logical block 498074
[17179783.148000] Buffer I/O error on device sda1, logical block 498072
[17179783.148000] Buffer I/O error on device sda1, logical block 498073
[17179783.148000] Buffer I/O error on device sda1, logical block 498074
[17179783.148000] Buffer I/O error on device sda1, logical block 498072
[17179783.148000] Buffer I/O error on device sda1, logical block 498073
[17179783.148000] Buffer I/O error on device sda1, logical block 498074
[17179783.148000] Buffer I/O error on device sda1, logical block 498072
[17179783.308000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[17179783.308000] sda: Write Protect is off
[17179783.308000] sda: Mode Sense: 03 00 00 00
[17179783.308000] sda: assuming drive cache: write through
[17179784.176000] end_request: I/O error, dev sda, sector 498173
[17179784.340000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[17179784.340000] sda: Write Protect is off
[17179784.340000] sda: Mode Sense: 03 00 00 00
[17179784.340000] sda: assuming drive cache: write through

```

And here's what happens when I click on the icon in Nautilus:

```

[17179810.016000] UDF-fs: No partition found (1)
[17179810.092000] Unable to identify CD-ROM format.

```

Note that it still seems to be complaining, and thinks that this is a CD-ROM, but the card does mount in this case and seems to work OK.

I think I'll move this over to bugzilla now - I'll do a Dapper hard disk install first so I've got a better platform to test it on. I'll post the bug number he4re when I've raised it.

I'm still interested in hearing from anyone else who is using SD cards with Ubuntu (Breezy or Dapper) - how well does it work?

Andy B

---

### Post by abovett on 2006-01-01
I've now raised this on bugzilla - [Bug 21762]("http://bugzilla.ubuntu.com/show_bug.cgi?id=21762").

Andy B

---

### Post by Aphorism on 2006-01-02
I was unable to see my cardreader which sounds similar.

I had to blacklist ehci_hcd as per the techs at bugzilla.  It worked fine after that.  Add it to your blacklist and see if it works for you after a reboot.

Good luck...

---

### Post by ryan76 on 2006-05-06
I have had this happen too - the cardreader worked fine for a few days and now it doesn't read any cards at all.

I'm a bit of a newbie and don't understand this... "blacklist ehci_hcd as per the techs at bugzilla" Can anyone please tell me what I can try?

Thanks

---

### Post by abies on 2006-06-17
I also want to get my SD cards read, and I also don't understand what this means.  Can anybody elaborate?

---

### Post by abovett on 2006-06-24
Before getting into the details of this - have you upgraded to Dapper or are you still on Breezy? I ask because as far as I can tell these problems have been solved in Dapper. I do find that it's best if I format the cards using the PC rather than letting my camera do it - you could try that if you're still having problems. I had to use fdisk and mkfs from the command line to "revive" one of my cards (cfdisk did not work) so if you are not confident at the command line and need help with this let me know and I'll post details of how I did it.

Andy B

---

