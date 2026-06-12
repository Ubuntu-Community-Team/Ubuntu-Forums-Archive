---
title: "garbled sound"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by spd106 on 2005-09-13
Hi, i'm having trouble with a USB cd-rewriter drive. When i plug it in to my laptop it make the sound go wierd. At first it will sound garbled in the right speaker then the right speaker goes out of sync and seems to play faster. After about a minute it's nearly a second ahead of the left speaker.

This happens when i try to play an audio cd from the USB drive. I've tried cd player and xmms. It will also happen in Rhythmbox and Totem with an ogg file from the hard drive.

When i play a cd from my internal dvd-rom drive using xmms and the Alsa or OSS output drivers it can play fine sometimes but not always. It seems quite hit and miss. With the esound driver though it always goes bad. If i change the input to analog in xmms it seems to work perfectly.

I have also tried internet streams through realplayer 8 and get intermittant results. Mostly similar to the dvd drive w/ digital input.

The usb drive is a Freecom FX-1 CD-RW and Ubuntu recognises it as a scsi drive. Also i found that it can't use the analog input driver in xmms.
The sound card is an ESS es1978 maestro 2E rev10 and it uses the es1968 driver as far as i know.
Here are the important parts of output from dmesg
```

...
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
PCI: setting IRQ 10 as level-triggered
PCI: Assigned IRQ 10 for device 0000:00:07.2
uhci_hcd 0000:00:07.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:07.2: irq 10, io base 0xf300
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
SCSI subsystem initialized
Initializing USB Mass Storage driver...
usb 1-2: new low speed USB device using uhci_hcd and address 3
piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usbcore: registered new driver hiddev
...
es1968: not attempting power management.
  Vendor: GENERIC   Model: FREECOM24B        Rev: 1.51
  Type:   CD-ROM                             ANSI SCSI revision: 00
usb-storage: device scan complete
sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 5
es1968: clocking to 48000
...
```

Just to recap this happens when the usb drive is plugged in. When removed the laptop works fine, i just want everything to work right together. Just as it did in windows.  

If anyone has any ideas i'd be glad of some help.

---

### Post by mlomker on 2005-09-13
The only thing that I can think of is that it's a throughput issue...but that does nothing to explain playing from the hard disk!

Have you set DMA and whatnot using **hdparm**..at least on the internal drive?  I've had throughput weirdness on the USB bus to a flash device, myself.

---

### Post by spd106 on 2005-09-14
I've enabled DMA on my internal DVD drive. It didn't have any effect. When I tried hdparm on the usb drive it didn't have an option for DMA. I think that as it is detected as a scsi drive it won't be supported.

Thanks for the input though.

I'm going of try this usb drive on another pc to see what happens. It's just kinda difficult when you're surrounded with windows pc owners that won't let you touch their setups.

---

### Post by spd106 on 2005-09-15
Ok i've tried it on a newer pc with an nforce2 motherboard and the AC '97 on board sound, The usb drive plays cds fine. I see no problems with it.
This leads me to believe the problem is with the laptop or more specifically perhaps the sound driver for the ESS es1978 sound chip.

---

