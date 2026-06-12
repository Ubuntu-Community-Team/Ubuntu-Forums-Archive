---
title: "Protable HD crash - how to retrieve data files?"
date: 2009-01-02
forum: Hardware
---

### Post by Vincent_Lin on 2009-01-02
Dear all,

I have a USB portable HD with WD 1200VE(5400 2.5" EIDE 120GB) HD in it.  Somehow it stopped working(meaning, it was working fine).  It is formatted in Ext3 file system.

I am using 8.10 on IBM T42 laptop.

When plugged in, dmesg shows

--------------------- dmesg ------------------
[27644.020230] usb 1-4: new high speed USB device using ehci_hcd and address 17
[27644.191275] usb 1-4: configuration #1 chosen from 1 choice
[27644.222590] scsi17 : SCSI emulation for USB Mass Storage devices
[27644.229228] usb-storage: device found at 17
[27644.229246] usb-storage: waiting for device to settle before scanning
[27649.228396] usb-storage: device scan complete
[27653.986151] scsi 17:0:0:0: Direct-Access                               0811 PQ: 0 ANSI: 0
[27654.007113] sd 17:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[27654.011847] sd 17:0:0:0: [sdb] READ CAPACITY(16) failed
[27654.011861] sd 17:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[27654.011874] sd 17:0:0:0: [sdb] Use 0xffffffff as device size
[27654.011885] sd 17:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[27654.014974] sd 17:0:0:0: [sdb] Test WP failed, assume Write Enabled
[27654.014991] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[27654.021847] sd 17:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[27654.028846] sd 17:0:0:0: [sdb] READ CAPACITY(16) failed
[27654.028861] sd 17:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[27654.028873] sd 17:0:0:0: [sdb] Use 0xffffffff as device size
[27654.028883] sd 17:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[27654.043351] sd 17:0:0:0: [sdb] Test WP failed, assume Write Enabled
[27654.043366] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[27654.043379]  sdb:<6>usb 1-4: reset high speed USB device using ehci_hcd and address 17
[27714.396072] usb 1-4: reset high speed USB device using ehci_hcd and address 17
[27744.640156] usb 1-4: reset high speed USB device using ehci_hcd and address 17
[27774.884072] usb 1-4: reset high speed USB device using ehci_hcd and address 17
[27805.128071] usb 1-4: reset high speed USB device using ehci_hcd and address 17
------------ end of dmesg  ---------------------

I need help.

Can someone kind enough tell me 
1).  Can I make it work again?  And how if it is possible?
2).  How can I retrieve the data files on the HD, if possible?
3).  If I have to send it to some agency for data retrieval, how much $ we are talking about, if data retrieval is possible?
4).  I guess I am also interested in why it happened, but I am really more interested to the data files in it.

Thanks for all.

Vincent Lin

---

### Post by jbrown96 on 2009-01-02
You should probably try ddrescue, but dd may work as well. I'm not familiar with ddrescue, so this is for dd only. 

1) Find your drive ```
sudo fdisk -l
``` You need the /dev/sda3 or whatever the device name is. For the rest of the guide, I will assume /dev/sda3, but replace with yours. 

2) Decide where you dump the drive. It needs at least as much space as the size of your entire drive (even if it is not all used). I'm going to assume another removable drive mounted at /media/disk

3) dump the drive. WARNING!!!!! Make sure you do not confuse the devices listed in the command. If you do, ALL your data will be lost forever. ```
sudo dd if=/dev/sda3 of=/media/disk/backup.img
```

4) mount the drive. ```
mkdir ./backup && sudo mount -t auto /media/disk/backup.img ./backup
``` If you get an error about it not being a block device, try adding ```
-o loop
``` to the end of the previous command

---

### Post by Vincent_Lin on 2009-01-02
Thanks, Jbrown.

However, 

sudo fdisk -l

did not give me the device name of the USB HD.  The HD is not seen anywhere.

Any other ideas?

Thanks again.

Vincent

---

### Post by Rohan Kapoor on 2009-01-02
> **Vincent_Lin said:**
> Thanks, Jbrown.

However, 

sudo fdisk -l

did not give me the device name of the USB HD.  The HD is not seen anywhere.

Any other ideas?

Thanks again.

Vincent
It sounds like your entire usb drive is dead. Try pluggin it in to any other Linux/Windows/Mac computers and see if they can detect it. If not it means that you have a dead drive. This means that recovering data is impossible and you will need to get a new harddrive.

---

### Post by Vincent_Lin on 2009-01-02
It does not sound good at all.

Thanks, anyway.

Vincent

---

### Post by Rohan Kapoor on 2009-01-02
> **Vincent_Lin said:**
> It does not sound good at all.

Thanks, anyway.

Vincent
No it doesn't. Sorry but that's what it looks like!

---

### Post by blueridgedog on 2009-01-02
> **Vincent_Lin said:**
> Thanks, Jbrown.

However, 

sudo fdisk -l

did not give me the device name of the USB HD.  The HD is not seen anywhere.

Any other ideas?

Thanks again.

Vincent

If you can't get it to work as a USB drive, you can still try and remove the IDE or SATA drive from the enclosure and attempt to mount it in a PC or another enclosure.  It may only be the USB enclosure that is broken.

---

### Post by jbrown96 on 2009-01-02
> **blueridgedog said:**
> If you can't get it to work as a USB drive, you can still try and remove the IDE or SATA drive from the enclosure and attempt to mount it in a PC or another enclosure.  It may only be the USB enclosure that is broken.

+1 
or it may be the controller but you would probably have to get an identical drive so the controller would work.

---

### Post by Rohan Kapoor on 2009-01-03
> **jbrown96 said:**
> +1 
or it may be the controller but you would probably have to get an identical drive so the controller would work.
That could also work, assuming he could find an identical controller.

---

### Post by Vincent_Lin on 2009-01-03
Thanks to all you guys.

I will try to mount it on my T42 and boot from CD to see how it works.

Vincent

---

### Post by Rohan Kapoor on 2009-01-03
> **Vincent_Lin said:**
> Thanks to all you guys.

I will try to mount it on my T42 and boot from CD to see how it works.

Vincent
Good Luck!

---

### Post by nick09 on 2009-01-03
Well you can take the HDD out of the casing and hook it up inside your computer(you can steal a connection from one of your CD drives). Your last hope is to look up a company that will extract the data from each platter. Its a costly alternative that could cost up to 10K depending on how bad you need the data, but its useful if you really need the data.

---

### Post by Rohan Kapoor on 2009-01-03
> **nick09 said:**
> Well you can take the HDD out of the casing and hook it up inside your computer(you can steal a connection from one of your CD drives). Your last hope is to look up a company that will extract the data from each platter. Its a costly alternative that could cost up to 10K depending on how bad you need the data, but its useful if you really need the data.
But for the cost (10K) it would only make sense for a large corporation or government agency or some filthy rich guy!

---

### Post by nick09 on 2009-01-03
> **darth-vader said:**
> But for the cost (10K) it would only make sense for a large corporation or government agency or some filthy rich guy!

No. My IT instructor once paid that much for data he really needed. It makes sense if you own a business that needs data to operate. Besides the equipment you would need would cost quite a bit and you need to keep a room sealed from the outside environment. If you were to open a HDD you can lose all the data just by mere particles in the air.

Which would you do? Lose a report for your business and end up doing all over again or save yourself time you don't have to redone work?

---

