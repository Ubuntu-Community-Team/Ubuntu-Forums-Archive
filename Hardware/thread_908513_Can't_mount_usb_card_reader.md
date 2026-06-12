---
title: "Can't mount usb card reader"
date: 2008-09-02
forum: Hardware
---

### Post by seattle vic on 2008-09-02
I'm trying to get ubuntu hardy to recognize my usb card reader.  It's been successful before, but not now.  If I plug in the kingston SD memory card, an entry for kingston will pop up under the "Places" menu, but clicking it will not mount the device.

Other useful info.  I am running virtualbox, but have the usb disabled.  I'm also running cups to a printer that uses usb.

If I run:
$ mount

it shows there is an entry under proc, which I don't understand:
(6th line down)
===========================================
/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /media/vista_drive1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/ubuntu_drive2 type ext3 (rw,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
=======================================================
Is the proc entry related to cups?

If I try and mount to /media/usb, it seems to take the command, but there is nothing showing up in nautilus.

Thanks in advance,

Vic

---

### Post by IntuitiveNipple on 2008-09-02
Vic, there will only be a successful mount if the device has a recognisable file-system on it.

Do you have another PC you can do a quick check on? Flash memory cards have an annoying tendency to develop faults when you least expect it.

Another check you can do is to monitor the kernel log whilst plugging in the device:
```

tail -f /var/log/kern.log

```
Plug it in and you should see a few messages appear. When they have stopped copy/paste the output to a text file in the Text Editor and save it, or paste it directly into a reply here.

It might give clues as whether the device is correctly discovered, if a file-system (or read errors) is found, etc.

---

### Post by seattle vic on 2008-09-02
> **IntuitiveNipple said:**
> Vic, there will only be a successful mount if the device has a recognisable file-system on it.

Do you have another PC you can do a quick check on? Flash memory cards have an annoying tendency to develop faults when you least expect it.

Another check you can do is to monitor the kernel log whilst plugging in the device:
```

tail -f /var/log/kern.log

```
Plug it in and you should see a few messages appear. When they have stopped copy/paste the output to a text file in the Text Editor and save it, or paste it directly into a reply here.

It might give clues as whether the device is correctly discovered, if a file-system (or read errors) is found, etc.

====================================================
OK, here's what it shows:

vic@dualserver:/etc$ tail -f /var/log/kern.log
Sep  2 12:23:30 dualserver kernel: [404795.339840] sd 17:0:0:0: [sdh] Mode Sense: 00 00 00 00
Sep  2 12:23:30 dualserver kernel: [404795.339842] sd 17:0:0:0: [sdh] Assuming drive cache: write through
Sep  2 12:23:30 dualserver kernel: [404795.347693] sd 17:0:0:0: [sdh] 1981728 512-byte hardware sectors (1015 MB)
Sep  2 12:23:30 dualserver kernel: [404795.349808] sd 17:0:0:0: [sdh] Write Protect is off
Sep  2 12:23:30 dualserver kernel: [404795.349811] sd 17:0:0:0: [sdh] Mode Sense: 00 00 00 00
Sep  2 12:23:30 dualserver kernel: [404795.349812] sd 17:0:0:0: [sdh] Assuming drive cache: write through
Sep  2 12:23:31 dualserver kernel: [404795.349816]  sdh: sdh1
Sep  2 12:23:31 dualserver kernel: [404795.434495] sd 17:0:0:0: [sdh] Attached SCSI removable disk
Sep  2 12:23:31 dualserver kernel: [404795.434540] sd 17:0:0:0: Attached scsi generic sg8 type 0
Sep  2 16:30:20 dualserver kernel: [419581.534363] usb 2-3.4: USB disconnect, address 17
Sep  2 16:31:17 dualserver kernel: [419638.748869] usb 2-3.4: new full speed USB device using ehci_hcd and address 18
Sep  2 16:31:18 dualserver kernel: [419638.859265] usb 2-3.4: configuration #1 chosen from 1 choice
Sep  2 16:31:18 dualserver kernel: [419638.864027] scsi18 : SCSI emulation for USB Mass Storage devices
Sep  2 16:31:18 dualserver kernel: [419638.865540] usb-storage: device found at 18
Sep  2 16:31:18 dualserver kernel: [419638.865543] usb-storage: waiting for device to settle before scanning
Sep  2 16:31:23 dualserver kernel: [419643.858483] usb-storage: device scan complete
Sep  2 16:31:23 dualserver kernel: [419643.860632] scsi 18:0:0:0: Direct-Access     LEXAR CF READER           1.00 PQ: 0 ANSI: 2
Sep  2 16:31:23 dualserver kernel: [419643.865578] sd 18:0:0:0: [sdh] 1981728 512-byte hardware sectors (1015 MB)
Sep  2 16:31:23 dualserver kernel: [419643.867701] sd 18:0:0:0: [sdh] Write Protect is off
Sep  2 16:31:23 dualserver kernel: [419643.867705] sd 18:0:0:0: [sdh] Mode Sense: 00 00 00 00
Sep  2 16:31:23 dualserver kernel: [419643.867707] sd 18:0:0:0: [sdh] Assuming drive cache: write through
Sep  2 16:31:23 dualserver kernel: [419643.875560] sd 18:0:0:0: [sdh] 1981728 512-byte hardware sectors (1015 MB)
Sep  2 16:31:23 dualserver kernel: [419643.877682] sd 18:0:0:0: [sdh] Write Protect is off
Sep  2 16:31:23 dualserver kernel: [419643.877685] sd 18:0:0:0: [sdh] Mode Sense: 00 00 00 00
Sep  2 16:31:23 dualserver kernel: [419643.877687] sd 18:0:0:0: [sdh] Assuming drive cache: write through
Sep  2 16:31:23 dualserver kernel: [419643.877692]  sdh: sdh1
Sep  2 16:31:23 dualserver kernel: [419643.962406] sd 18:0:0:0: [sdh] Attached SCSI removable disk
Sep  2 16:31:23 dualserver kernel: [419643.962482] sd 18:0:0:0: Attached scsi generic sg8 type 0

---

### Post by jaouen on 2012-10-26
I have the same problem here, usb card reader doesn't auto-mount in /media.
From the kern.log, you know the device name (in your case: sdh1).
So you can mount it manually.

Only once, create a mount point in /mnt (i prefer to leave the /media for things the OS auto-mounts):
[I] sudo mkdir /mnt/usb
[/I] 
Then mount:
[I] sudo mount /dev/sdh1 /mnt/usb
[/I] 
It then shows up in nautilus (or whatever) in the regular file system, not as a specific device.

For shortcuts, add in /etc/fstab:
[I]# usb card reader
/dev/sdh1    /mnt/usb    vfat    rw,suid,dev,exec,noauto,nouser,async,uid=myuser,gid=mygroup  0       0
[/I] 
(replace myuser and mygroup by your user/group)

And next time "simply" do:
*sudo mount /mnt/usb*

---

### Post by lisati on 2012-10-26
A lot can change in four years.

Thread closed.

---

