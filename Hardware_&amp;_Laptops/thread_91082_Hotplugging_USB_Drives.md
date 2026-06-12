---
title: "Hotplugging USB Drives"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by suRoot on 2005-11-16
Has anyone else had problems with removable USB drives & Breezy?  I mean, all of mine work fine, but I always have to unplug the things & plug them back in after rebooting the box.  Has been that way since I installed Ubuntu.  I'm running a 2.6.14 kernel, but I don't think that's the issue as I see the same thing happen with the stock Ubuntu kernel.

Basically, I power up my system, log in to Gnome & don't see any of my USB drives on the desktop.  Okay... the mount command doesn't show them as being mounted.  Try to mount one:

```
mount /dev/sda1 /media/usbdisk
```

Tells me that /dev/sda1 is already mounted (no it isn't!  I just checked!)

Check dmesg & it shows the device as being recognized & that it's sda (or whatever depending upon how many drives I happen to have plugged in).

Unplug the drive, plug it back in & wham, I get the icon on my desktop & mount shows it mounted.

What gives?  It really isn't a big deal, but it's kind of a PITA having to unplug the drives everytime I boot (luckily not that often).

Thought maybe it had to do with my USB hub, but see the same thing plugged in to the USB port on the PC.

---

### Post by jeffjj on 2005-11-17
I get that same problem with my new iAudio G3 MP3/OGG player. I plug it in and nothing happens. I check the logs and it tells me a new usb device connected, but still nothing to click on. I try mounting it and it says nothing is there. If I unplug and then plug it back in a few times eventually I get an icon that is fully mounted and things are great. Very sparatic. After it mounts I look and it is on /dev/sda. I have been searching the forums and this seems to be a common problem with USB devices, but this posting sounded exactly like my problem.

---

### Post by gmc on 2005-11-17
[QUOTE=jeffjj]I get that same problem with my new iAudio G3 MP3/OGG player. I plug it in and nothing happens. I check the logs and it tells me a new usb device connected, but still nothing to click on. I try mounting it and it says nothing is there. If I unplug and then plug it back in a few times eventually I get an icon that is fully mounted and things are great. Very sparatic. After it mounts I look and it is on /dev/sda. I have been searching the forums and this seems to be a common problem with USB devices, but this posting sounded exactly like my problem.[/QUOTE]

I just rebooted with my usbhd plugged in and I don't have any problems. I recall rebooting with a usbflashdrive and it also is recognized.

[4294681.932000] Initializing USB Mass Storage driver...
[4294681.933000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294681.933000] usb-storage: device found at 2
[4294681.933000] usb-storage: waiting for device to settle before scanning
[4294681.933000] usbcore: registered new driver usb-storage
[4294681.933000] USB Mass Storage support registered.
[4294681.962000] usbcore: registered new driver hiddev
[4294681.982000] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1f.2-2
[4294681.982000] usbcore: registered new driver usbhid
[4294681.982000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver

Also you might want to check that you have /apps/nautilus/desktop/volumes_visible checked active in the Configuration Editor.

I do have mounting problems if I use a custom 2.6.14 kernel, but I belive that's a pmount problem. There is information on upgrading this package else where in the Ubuntu Forums.

G.

---

### Post by gmc on 2005-11-17
[QUOTE=suRoot]Has anyone else had problems with removable USB drives & Breezy?  I mean, all of mine work fine, but I always have to unplug the things & plug them back in after rebooting the box.  Has been that way since I installed Ubuntu.  I'm running a 2.6.14 kernel, but I don't think that's the issue as I see the same thing happen with the stock Ubuntu kernel.

Basically, I power up my system, log in to Gnome & don't see any of my USB drives on the desktop.  Okay... the mount command doesn't show them as being mounted.  Try to mount one:

```
mount /dev/sda1 /media/usbdisk
```

Tells me that /dev/sda1 is already mounted (no it isn't!  I just checked!)

Check dmesg & it shows the device as being recognized & that it's sda (or whatever depending upon how many drives I happen to have plugged in).

Unplug the drive, plug it back in & wham, I get the icon on my desktop & mount shows it mounted.

What gives?  It really isn't a big deal, but it's kind of a PITA having to unplug the drives everytime I boot (luckily not that often).

Thought maybe it had to do with my USB hub, but see the same thing plugged in to the USB port on the PC.[/QUOTE]

How long is the usb cable/hub total? I'm wondering if maybe that's a problem. As I say, I don't seem to have any problems accessing my usbhd either after a reboot or hotplugging it in.

G.

---

### Post by Cyrus on 2005-11-17
Not quite as your problem, but:

I am using a USB CD-Drive. Everything worked fine until today. I bought a USB-Backup-HD. After plugging it in, this also worked, but suddenly the CD-Drive is not working anymore ...

Unpluging the HD and replugging the CD-Drive makes my old system to work, but I need to have them working side by side.

ok, this is the dmesg when plugging in the CD Drive only

```
[4298522.520000] usb 5-3: new high speed USB device using ehci_hcd and address 21
[4298522.646000] scsi13 : SCSI emulation for USB Mass Storage devices
[4298522.647000] usb-storage: device found at 21
[4298522.647000] usb-storage: waiting for device to settle before scanning
[4298527.678000]   Vendor: PLEXTOR   Model: CD-R   PX-230A    Rev: 1.00
[4298527.678000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[4298528.520000] sr0: scsi3-mmc drive: 0x/52x writer cd/rw xa/form2 cdda tray
[4298528.521000] Attached scsi CD-ROM sr0 at scsi13, channel 0, id 0, lun 0
[4298528.522000] Attached scsi generic sg2 at scsi13, channel 0, id 0, lun 0,  type 5
[4298528.523000] usb-storage: device scan complete

```
this comes when also plugging in the usb hd
```
[4298644.770000] usb 5-7: new high speed USB device using ehci_hcd and address 22
[4298644.868000] scsi14 : SCSI emulation for USB Mass Storage devices
[4298644.869000] usb-storage: device found at 22
[4298644.869000] usb-storage: waiting for device to settle before scanning
[4298649.869000]   Vendor: Maxtor 6  Model: L100P0            Rev: BAH4
[4298649.869000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4298649.873000] SCSI device sdc: 195813072 512-byte hdwr sectors (100256 MB)
[4298649.873000] sdc: assuming drive cache: write through
[4298649.874000] SCSI device sdc: 195813072 512-byte hdwr sectors (100256 MB)
[4298649.874000] sdc: assuming drive cache: write through
[4298649.874000]  /dev/scsi/host14/bus0/target0/lun0: p1
[4298649.899000] Attached scsi disk sdc at scsi14, channel 0, id 0, lun 0
[4298649.900000] Attached scsi generic sg3 at scsi14, channel 0, id 0, lun 0,  type 0
[4298649.901000] usb-storage: device scan complete
[4298650.240000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```
and this comes when I try to access the cd-drive /dev/scd0
```
[4298720.217000] usb 5-3: reset high speed USB device using ehci_hcd and address 21
[4298736.368000] scsi: Device offlined - not ready after error recovery: host 13 channel 0 id 0 lun 0
[4298736.368000] scsi13 (0:0): rejecting I/O to offline device
[4298736.368000] scsi13 (0:0): rejecting I/O to offline device
[4298736.368000] scsi13 (0:0): rejecting I/O to offline device
[4298736.368000] scsi13 (0:0): rejecting I/O to offline device

```

Why is the device offlined? Any ideas?

---

### Post by jeffjj on 2005-11-17
Thanks for the replys!

I searched the forums again this morning and I believe this is exactly what I was looking for  [http://ubuntuforums.org/showthread.php?t=81836&highlight=usb](http://ubuntuforums.org/showthread.php?t=81836&highlight=usb)

I am going to test tonight or tommorrow and will report my findings, but it looks like this is a known issue.

---

### Post by gmc on 2005-11-19
[QUOTE=Cyrus]Not quite as your problem, but:

I am using a USB CD-Drive. Everything worked fine until today. I bought a USB-Backup-HD. After plugging it in, this also worked, but suddenly the CD-Drive is not working anymore ...

(edited for beverity)

Why is the device offlined? Any ideas?[/QUOTE]

I'm not sure but it sound like something to do with a limitation on your usb ports (or chipset). What kind of machine are we talking about here? If you had asked about this a few years ago I might have thought that the port couldn't supply enough power to power both devices, but since both peripherals are self powered it can't be that.

G.

---

### Post by gmc on 2005-11-19
[QUOTE=jeffjj]Thanks for the replys!

I searched the forums again this morning and I believe this is exactly what I was looking for  [http://ubuntuforums.org/showthread.php?t=81836&highlight=usb](http://ubuntuforums.org/showthread.php?t=81836&highlight=usb)

I am going to test tonight or tommorrow and will report my findings, but it looks like this is a known issue.[/QUOTE]

How did you make out? Is it working.

G.

---

### Post by Cyrus on 2005-11-21
Hmm, it is a very new Dell machine:

Intel Pentium 4 - 3,2 GHz (1024 KB cache), 512 MB RAM.

And yes they are both seperately powered. Any other ideas?

---

### Post by phanboy_iv on 2005-11-21
I've had some weird USB issues with my flash drive too. Actually, this was a problem for me in Hoary as well. I've tried the "give yourself access permissions" trick, and that generally works fine, but some times I still have to unplug/reinsert  the flash drive to get it to show up. And if it's plugged in at boot, it won't show up untill I reinsert it. Come to think of it, occasionally I get some CDROM automount weirdness, too. But automount works for me about 8/10 times, so I guess filing a bug and being happy is my best plan.

---

### Post by suRoot on 2005-11-21
[QUOTE=gmc]How long is the usb cable/hub total? I'm wondering if maybe that's a problem. As I say, I don't seem to have any problems accessing my usbhd either after a reboot or hotplugging it in.

G.[/QUOTE]


None of the cables are more than two feet long.  USB hub was also bypassed & devices plugged directly in to port on laptop (IBM T40p).

Interesting thing was that update manager found available updates for my machine a few days ago & after installing them I no longer see this problem (on any of my kernels).  Unfortunately I really didn't pay attention to which updates were being installed, so I'm not sure which of them fixed it (assuming one of them did).  I haven't seen the problem in a few days, which is good news for me.

---

### Post by sporniket on 2006-05-18
[QUOTE=Cyrus]Not quite as your problem, but:

I am using a USB CD-Drive. Everything worked fine until today. I bought a USB-Backup-HD. After plugging it in, this also worked, but suddenly the CD-Drive is not working anymore ...

Unpluging the HD and replugging the CD-Drive makes my old system to work, but I need to have them working side by side.

ok, this is the dmesg when plugging in the CD Drive only

*etc...*

Why is the device offlined? Any ideas?[/QUOTE]

Since I upgraded yesterday from Warty to Hoary than Breezy, I experience the same trouble with my external Lacie USB2 HardDrive. It was working perfectly with Warty (4.10)

```
[4295982.260000] scsi1 : SCSI emulation for USB Mass Storage devices
[4295982.263000] usb-storage: device found at 8
[4295982.263000] usb-storage: waiting for device to settle before scanning
[4295987.263000]   Vendor: WDC WD16  Model: 00BB-00FTA0       Rev: 15.0
[4295987.263000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4295987.282000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4295987.282000] sda: assuming drive cache: write through
[4295987.287000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4295987.287000] sda: assuming drive cache: write through
[4295987.287000]  /dev/scsi/host1/bus0/target0/lun0: p1 p2
[4295987.299000] Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
[4296063.363000] usb 5-3: reset high speed USB device using ehci_hcd and address 8
[4296066.425000] usb 5-3: device descriptor read/64, error -110
[4296081.598000] usb 5-3: device descriptor read/64, error -110
[4296081.761000] usb 5-3: reset high speed USB device using ehci_hcd and address 8
[4296084.823000] usb 5-3: device descriptor read/64, error -110
[4296099.986000] usb 5-3: device descriptor read/64, error -110
[4296100.149000] usb 5-3: reset high speed USB device using ehci_hcd and address 8
[4296105.162000] usb 5-3: device descriptor read/8, error -110
[4296110.277000] usb 5-3: device descriptor read/8, error -110
[4296110.440000] usb 5-3: reset high speed USB device using ehci_hcd and address 8
[4296115.452000] usb 5-3: device descriptor read/8, error -110
[4296120.564000] usb 5-3: device descriptor read/8, error -110
[4296120.665000] scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0

```

---

