---
title: "USB Issues abound"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by msollie on 2007-01-15
Hello,

I could really use some help here.

This started off when I upgraded from 6.06 (which almost worked perfectly) to 6.10 which gave me the "Failed to initialize HAL!" message on the first boot and every subsequent boot.

It's only gone down hill.

1.) Still have the "Failed to initialize HAL!" message
2.) External HD, Printer, and mouse don't show up on boot
3.) lsusb produces no output
4.) Device Manager doesn't start

I've reinstalled almost everything in Synaptic having to do with USB, dbus, device-manager, gnome-volume-manager, etc.

I'm using an IBM Thinkpad with Ubuntu for about 6 months.  Ubuntu has never worked perfect, but this is driving me NUTS.  Any help would be appreciated.

Matt

msollie@Sollie:~$ lspci
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
00:03.1 Serial controller: Agere Systems LT WinModem (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
```

No output???
```

msollie@Sollie:~$ lsusb
```

But the USB stuff (HD, printer, mouse, etc.) are all there according to lspci

msollie@Sollie:~$ tail -f /var/log/syslog
```
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readwrite:/home/msollie/.gconf" to a writable configuration source at position 1
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readonly:/usr/local/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readwrite:/home/msollie/.gconf" to a writable configuration source at position 3
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 4
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 5
Jan 15 20:06:04 localhost gconfd (msollie-4544): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 6
Jan 15 20:14:25 localhost kernel: [4296529.032000] usb 1-1.1: new low speed USB device using uhci_hcd and address 5
Jan 15 20:14:25 localhost kernel: [4296529.215000] input: USB HID v1.00 Mouse [Fellowes Corp. Mini Optical RF] on usb-0000:00:07.2-1.1
Jan 15 20:17:02 localhost /USR/SBIN/CRON[6959]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 15 20:19:26 localhost kernel: [4296830.142000] usb 1-1: USB disconnect, address 2
Jan 15 20:19:26 localhost kernel: [4296830.142000] usb 1-1.1: USB disconnect, address 5
Jan 15 20:19:26 localhost kernel: [4296830.142000] usb 1-1.2: USB disconnect, address 3
Jan 15 20:19:26 localhost kernel: [4296830.144000] usb 1-1.4: USB disconnect, address 4
Jan 15 20:19:39 localhost kernel: [4296843.058000] usb 1-1: new full speed USB device using uhci_hcd and address 6
Jan 15 20:19:39 localhost kernel: [4296843.240000] hub 1-1:1.0: USB hub found
Jan 15 20:19:39 localhost kernel: [4296843.242000] hub 1-1:1.0: 4 ports detected
Jan 15 20:19:40 localhost kernel: [4296843.481000] usb 1-1.2: new full speed USB device using uhci_hcd and address 7
Jan 15 20:19:40 localhost kernel: [4296843.536000] scsi2 : SCSI emulation for USB Mass Storage devices
Jan 15 20:19:40 localhost kernel: [4296843.536000] usb-storage: device found at 7
Jan 15 20:19:40 localhost kernel: [4296843.536000] usb-storage: waiting for device to settle before scanning
Jan 15 20:19:40 localhost kernel: [4296843.670000] usb 1-1.4: new full speed USB device using uhci_hcd and address 8
Jan 15 20:19:40 localhost kernel: [4296844.283000] scsi3 : SCSI emulation for USB Mass Storage devices
Jan 15 20:19:40 localhost kernel: [4296844.283000] usb-storage: device found at 8
Jan 15 20:19:40 localhost kernel: [4296844.283000] usb-storage: waiting for device to settle before scanning
Jan 15 20:19:40 localhost kernel: [4296844.289000] hiddev96: USB HID v1.10 Device [Western Digital External HDD] on usb-0000:00:07.2-1.4
Jan 15 20:19:41 localhost kernel: [4296844.422000] usb 1-1.1: new low speed USB device using uhci_hcd and address 9
Jan 15 20:19:41 localhost kernel: [4296844.535000] input: USB HID v1.00 Mouse [Fellowes Corp. Mini Optical RF] on usb-0000:00:07.2-1.1
Jan 15 20:19:45 localhost kernel: [4296848.539000]   Vendor: HP        Model: Photosmart 8100   Rev: 1.00
Jan 15 20:19:45 localhost kernel: [4296848.539000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Jan 15 20:19:45 localhost kernel: [4296848.554000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Jan 15 20:19:45 localhost kernel: [4296848.555000] usb-storage: device scan complete
Jan 15 20:19:45 localhost kernel: [4296849.289000]   Vendor: WD        Model: 1200BB External   Rev: 0412
Jan 15 20:19:45 localhost kernel: [4296849.289000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 15 20:19:45 localhost kernel: [4296849.296000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
Jan 15 20:19:45 localhost kernel: [4296849.296000] sdb: assuming drive cache: write through
Jan 15 20:19:45 localhost kernel: [4296849.301000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
Jan 15 20:19:45 localhost kernel: [4296849.301000] sdb: assuming drive cache: write through
Jan 15 20:19:45 localhost kernel: [4296849.301000]  /dev/scsi/host3/bus0/target0/lun0: p1
Jan 15 20:19:45 localhost kernel: [4296849.326000] Attached scsi disk sdb at scsi3, channel 0, id 0, lun 0
Jan 15 20:19:45 localhost kernel: [4296849.327000] usb-storage: device scan complete
```

---

### Post by msollie on 2007-01-20
BUMP!

Would it help if i posted my fstab?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0   $
#/dev/sda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda        /media/usb0     auto rw,user,noauto 0 0
/dev/sda1       /media/windows vfat umask=0     0       0        0       0
/dev/sda2       /media/usb1     auto rw,user,noauto 0 0
/dev/sda3       /media/windows2 vfat umask=0    0       0        0       0
```

Any help here??

---

### Post by tweedledee on 2007-01-21
Probably not what you want to hear, but the only way I could clear that error on one my computers was to finally give up and do a fresh install.  There might be another way to deal with it, but I couldn't find it.

---

### Post by msollie on 2007-01-24
Ok, I just did a clean install.  But I did it using a PXE Ubuntu Network install using a Windows DHCPTFTP machine...kinda cool!

Thanks,

Matt

---

