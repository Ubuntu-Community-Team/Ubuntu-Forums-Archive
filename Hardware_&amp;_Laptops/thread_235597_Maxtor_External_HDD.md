---
title: "Maxtor External HDD"
date: 2006-08-13
forum: Hardware &amp; Laptops
---

### Post by Mystify on 2006-08-13
I was once before able to access my external hdd just fine and play music/videos off of it.

Earlier this morning I tried to access it and get this error

[IMG]http://i7.tinypic.com/24gsqc5.png[/IMG]

I switched back over to windows XP to make sure the HDD wasn't corrupted but it came up just fine and was able to access the files.

I even tried putting my profile into the root group and still get the same error.

Anyone know of any solutions for this? ](*,)

---

### Post by jordilin on 2006-08-13
I would reboot with the hard drive unplugged, then once you are in Ubuntu, plug it again. Ubuntu should mount it automatically. What kind of filesystem format has your external drive?

---

### Post by Mystify on 2006-08-13
Already tried that ... and it is in Windows NTFS format.

---

### Post by jordilin on 2006-08-13
Copy and paste what /var/log/messages says when trying to mount the harddrive. Only paste the relevant info.

---

### Post by Mystify on 2006-08-13
Aug 13 12:54:28 mystify kernel: [17179654.432000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 13 12:54:28 mystify kernel: [17179654.708000] SCSI subsystem initialized
Aug 13 12:54:28 mystify kernel: [17179654.760000] Initializing USB Mass Storage driver...
Aug 13 12:54:28 mystify kernel: [17179654.760000] scsi0 : SCSI emulation for USB Mass Storage devices
Aug 13 12:54:28 mystify kernel: [17179654.760000] usbcore: registered new driver usb-storage
Aug 13 12:54:28 mystify kernel: [17179654.760000] USB Mass Storage support registered.
Aug 13 12:54:34 mystify kernel: [17179660.624000]   Vendor: Maxtor    Model: 3200              Rev: 0341
Aug 13 12:54:34 mystify kernel: [17179660.624000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Aug 13 12:54:34 mystify kernel: [17179660.680000] Driver 'sd' needs updating - please use bus_type methods
Aug 13 12:54:34 mystify kernel: [17179660.680000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
Aug 13 12:54:34 mystify kernel: [17179660.680000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
Aug 13 12:54:34 mystify kernel: [17179660.680000]  sda: sda1
Aug 13 12:54:34 mystify kernel: [17179660.716000] sd 0:0:0:0: Attached scsi disk sda
Aug 13 12:54:34 mystify kernel: [17179660.728000] sd 0:0:0:0: Attached scsi generic sg0 type 0

---

### Post by jordilin on 2006-08-13
> **Mystify said:**
> Aug 13 12:54:28 mystify kernel: [17179654.432000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 13 12:54:28 mystify kernel: [17179654.708000] SCSI subsystem initialized
Aug 13 12:54:28 mystify kernel: [17179654.760000] Initializing USB Mass Storage driver...
Aug 13 12:54:28 mystify kernel: [17179654.760000] scsi0 : SCSI emulation for USB Mass Storage devices
Aug 13 12:54:28 mystify kernel: [17179654.760000] usbcore: registered new driver usb-storage
Aug 13 12:54:28 mystify kernel: [17179654.760000] USB Mass Storage support registered.
Aug 13 12:54:34 mystify kernel: [17179660.624000]   Vendor: Maxtor    Model: 3200              Rev: 0341
Aug 13 12:54:34 mystify kernel: [17179660.624000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Aug 13 12:54:34 mystify kernel: [17179660.680000] Driver 'sd' needs updating - please use bus_type methods
Aug 13 12:54:34 mystify kernel: [17179660.680000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
Aug 13 12:54:34 mystify kernel: [17179660.680000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
Aug 13 12:54:34 mystify kernel: [17179660.680000]  sda: sda1
Aug 13 12:54:34 mystify kernel: [17179660.716000] sd 0:0:0:0: Attached scsi disk sda
Aug 13 12:54:34 mystify kernel: [17179660.728000] sd 0:0:0:0: Attached scsi generic sg0 type 0

It seems that is correctly detected and mounted. Do you see any folder in the Desktop, as if the drive got mounted?

---

### Post by Mystify on 2006-08-13
[IMG]http://i8.tinypic.com/24gvzvd.png[/IMG]




It detects it as that ... But when it use to work it came up as the actual HDD's name.

It is the 93.4 GB Volume.

---

### Post by jordilin on 2006-08-13
take a look at the following thread. There was a guy who had the same problem  as you:
[http://www.ubuntuforums.org/showthread.php?t=223657](http://www.ubuntuforums.org/showthread.php?t=223657)

---

### Post by Mystify on 2006-08-13
```
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
```


That made it work :p

---

### Post by fazofazo on 2006-08-13
I can hdd format c:/ or d:/ ot fdisk :(

---

### Post by jordilin on 2006-08-13
> **Mystify said:**
> ```
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
```


That made it work :p

Ok, very good, \\:D/

---

