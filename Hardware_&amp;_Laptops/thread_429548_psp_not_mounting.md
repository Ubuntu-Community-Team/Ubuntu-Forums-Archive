---
title: "psp not mounting"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by BU5T4 on 2007-05-01
Hi Guys,

I'm having some problems with mounting my psp after re-installing Ubuntu. I was having major problems with my install of gdm so created a new /home parttion and then re-installed the os.

Everything (except my wireless) is working but when i plug in my psp it doesnt show up on the desktop anymore which it did before.

when i look in device manager the psp is detected.

I get this at the bottom of dmesg when i plug it in

```

[130852.020000] usb 5-1: new high speed USB device using ehci_hcd and address 13
[130852.152000] usb 5-1: configuration #1 chosen from 1 choice
[130852.152000] scsi16 : SCSI emulation for USB Mass Storage devices
[130852.152000] usb-storage: device found at 13
[130852.152000] usb-storage: waiting for device to settle before scanning
[130857.152000] usb-storage: device scan complete
[130857.152000] scsi 16:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[130857.152000] SCSI device sdb: 7954432 512-byte hdwr sectors (4073 MB)
[130857.152000] sdb: Write Protect is off
[130857.152000] sdb: Mode Sense: 00 6a 20 00
[130857.152000] sdb: assuming drive cache: write through
[130857.156000] SCSI device sdb: 7954432 512-byte hdwr sectors (4073 MB)
[130857.156000] sdb: Write Protect is off
[130857.156000] sdb: Mode Sense: 00 6a 20 00
[130857.156000] sdb: assuming drive cache: write through
[130857.156000]  sdb: sdb1
[130857.156000] sd 16:0:0:0: Attached scsi removable disk sdb
[130857.156000] sd 16:0:0:0: Attached scsi generic sg2 type 0
[130916.980000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[130961.960000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[131085.180000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[131182.896000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[131208.436000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


```

and lsusb shows this

```

Bus 005 Device 013: ID 054c:01c8 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

Any idea what could be causing this?

Thanks 

D-A

---

### Post by taurus on 2007-05-01
What happens when you run (from a terminal)

```
sudo mkdir /media/psp
sudo mount -t vfat /dev/sdb1 /media/psp -o iocharset=utf8,umask=000
df -h
```

---

### Post by BU5T4 on 2007-05-01
> **taurus said:**
> What happens when you run (from a terminal)

```
sudo mkdir /media/psp
sudo mount -t vfat /dev/sdb1 /media/psp -o iocharset=utf8,umask=000
df -h
```

Taurus your a genius. That seems to have done the trick. Thanks alot.

Will I have to add in that line to my fstab to get it to do this all the time?

Any idea why it doesn't come up automatically when it did before the re-install?

Thanks again for the help.

D-A

---

### Post by taurus on 2007-05-01
If you want to add that to your /etc/fstab, then the entry for it should look like this.

```
/dev/sdb1    /media/psp   vfat    iocharset=utf8,umask=000   0   0
```

---

### Post by BU5T4 on 2007-05-01
Brilliant mate thank you so much for the super quick reply.

That seems to have done the trick and I've added it to my fstab file.

Thanks alot

D-A

---

### Post by megamik79 on 2007-05-01
> **BU5T4 said:**
> 
Any idea why it doesn't come up automatically when it did before the re-install?


Maybe your problem is related to [the thread "Devices no longer automount, including USB drive and mmcdisk"]("http://ubuntuforums.org/showthread.php?t=403725").

---

