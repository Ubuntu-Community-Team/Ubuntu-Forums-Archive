---
title: "Problem with the new hard disk"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by Stefano Baghino on 2007-11-11
Hi there, everybody. I have a problem which may be related to the new hard disk. One year ago my laptop (Acer TravelMate 650) had some problems: the filesystem went corrupted, so the technician who repaired it decided to replace it (although it was possible just to format the original one). Now: since then I experienced problems both with Windows and Linux. The problem's the same: USB devices (the mouse in particular) occasionally disconnect. In Windows it was possible that the peripheral automatically reconnected or you got to phisically unplug and plug it back in. Now, in Linux, the mouse simply stops working. I have 4 USB ports: it may work a little longer if I plug it in ports 3 or 4, but after a while the same problem occurs and even plugging it back in ports 1 or 2 doesn't work.

The first piece of information was that there was a possible IRQ conflict:

```
root@mark:~# cat /proc/interrupts 
           CPU0       
  0:     693440    XT-PIC-XT        timer
  1:       9223    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:      34957    XT-PIC-XT        uhci_hcd:usb2, eth0
  7:          3    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:       6268    XT-PIC-XT        acpi
 10:     274244    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb3, uhci_hcd:usb4, ohci1394, ehci_hcd:usb5, yenta, yenta, Intel 82801CA-ICH3, radeon@pci:0000:01:00.0
 12:        603    XT-PIC-XT        i8042
 14:      60544    XT-PIC-XT        libata
 15:      40620    XT-PIC-XT        libata
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0
```

As you can see, there are to IRQs reserved to *libata*. I thought that prior to the hard disk replacing I had an IDE device (/dev/hda) while now I have an ATA device:

```
root@mark:~# hdparm -iI /dev/sda

/dev/sda:

 Model=SAMSUNG HM080HC                         , FwRev=AM100-16, SerialNo=S0CCJ20P130643      
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
        Model Number:       SAMSUNG HM080HC                         
        Serial Number:      S0CCJ20P130643      
        Firmware Revision:  AM100-16
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 0 
        Supported: 7 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        LBA48  user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0080)
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Advanced Power Management feature set
           *    SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    IDLE_IMMEDIATE with UNLOAD
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        44min for SECURITY ERASE UNIT. 44min for ENHANCED SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct
```

So, after all this, my conclusion is that the problem is a conflict between the ATA device and the USB hub.
Do you think my diagnosis is correct? If so, is there a way to fix the problem without putting back my old IDE drive (which I currently use for backups?

Thanks in advance to everyone! :)

---

### Post by kevinatkins on 2007-11-11
Hi there,

I doubt it's the libata IRQ's - 14 and 15 are used by the two IDE channels on most motherboards I think so your problem is elsewhere I think, unfortunately...

It's difficult to offer any more advice though - it certainly looks like a hardware problem, given that Windows and Linux are affected equally, but tracking it down might be quite difficult..

I'd make use of the excellent logging in Linux - have a look in /var/log/messages for a start and see if there's anything suspicious in there....

Good luck!

---

### Post by Stefano Baghino on 2007-11-11
I will, thanks. Meanwhile I'll add this: I put back the original hard disk and installed Ubuntu on it. Again my ATA device is seen as a SCSI one (/dev/sda). The drive works fine, but this shouldn't be! I still remember when I installed other Linux distros on the old hard disk (the one that I just put back in place) it was seen as an IDE device. Isn't it strange?!?

---

### Post by kevinatkins on 2007-11-11
Hi,

Don't worry - this is as it should be... from Feisty onwards I think, libata now classes IDE devices as SCSI, or something like that, so what would have been /dev/hda will now appear as /dev/sda... that little thing had me scratching my head, too, for a while....;-)

---

### Post by Stefano Baghino on 2007-11-11
Here's what I got from */var/log/messages* about the USB device:

```
Nov 11 18:19:17 mark kernel: [ 1085.444000] usb 4-2: USB disconnect, address 2
Nov 11 18:19:17 mark kernel: [ 1085.684000] usb 4-2: new low speed USB device using uhci_hcd and address 3
Nov 11 18:19:17 mark kernel: [ 1085.860000] usb 4-2: configuration #1 chosen from 1 choice
Nov 11 18:19:17 mark kernel: [ 1085.888000] input: Magic ball Mouse Magic ball Mouse as /class/input/input8
Nov 11 18:19:17 mark kernel: [ 1085.888000] input: USB HID v1.10 Mouse [Magic ball Mouse Magic ball Mouse] on usb-0000:02:09.1-2
Nov 11 18:28:03 mark kernel: [ 1611.124000] usb 4-2: USB disconnect, address 3
Nov 11 18:28:03 mark kernel: [ 1611.364000] usb 4-2: new low speed USB device using uhci_hcd and address 4
Nov 11 18:28:03 mark kernel: [ 1611.540000] usb 4-2: configuration #1 chosen from 1 choice
Nov 11 18:28:03 mark kernel: [ 1611.568000] input: Magic ball Mouse Magic ball Mouse as /class/input/input9
Nov 11 18:28:03 mark kernel: [ 1611.568000] input: USB HID v1.10 Mouse [Magic ball Mouse Magic ball Mouse] on usb-0000:02:09.1-2
Nov 11 18:41:41 mark -- MARK --
Nov 11 18:50:16 mark kernel: [ 2944.612000] usb 4-2: USB disconnect, address 4
Nov 11 18:50:16 mark kernel: [ 2944.852000] usb 4-2: new low speed USB device using uhci_hcd and address 5
Nov 11 18:50:17 mark kernel: [ 2945.028000] usb 4-2: configuration #1 chosen from 1 choice
Nov 11 18:50:17 mark kernel: [ 2945.052000] input: Magic ball Mouse Magic ball Mouse as /class/input/input10
Nov 11 18:50:17 mark kernel: [ 2945.052000] input: USB HID v1.10 Mouse [Magic ball Mouse Magic ball Mouse] on usb-0000:02:09.1-2
Nov 11 18:52:25 mark kernel: [ 3073.596000] usb 4-2: USB disconnect, address 5
Nov 11 18:52:25 mark kernel: [ 3074.032000] usb 4-2: new low speed USB device using uhci_hcd and address 6
Nov 11 18:52:56 mark kernel: [ 3104.864000] usb 4-2: new low speed USB device using uhci_hcd and address 7
Nov 11 18:53:27 mark kernel: [ 3135.860000] usb 4-2: new low speed USB device using uhci_hcd and address 8
Nov 11 18:53:38 mark kernel: [ 3146.684000] usb 4-2: new low speed USB device using uhci_hcd and address 9
Nov 11 18:53:51 mark kernel: [ 3159.416000] usb usb4: Controller not stopped yet!
Nov 11 19:21:41 mark -- MARK --
Nov 11 19:41:41 mark -- MARK --
Nov 11 20:01:41 mark -- MARK --
Nov 11 20:21:41 mark -- MARK --
Nov 11 20:41:41 mark -- MARK --
Nov 11 21:01:41 mark -- MARK --
Nov 11 21:21:41 mark -- MARK --
Nov 11 21:41:41 mark -- MARK --
Nov 11 22:01:41 mark -- MARK --
Nov 11 22:09:33 mark kernel: [14901.476000] usb 3-2: new low speed USB device using uhci_hcd and address 2
Nov 11 22:09:33 mark kernel: [14901.652000] usb 3-2: configuration #1 chosen from 1 choice
Nov 11 22:09:33 mark kernel: [14901.680000] input: Magic ball Mouse Magic ball Mouse as /class/input/input11
Nov 11 22:09:33 mark kernel: [14901.680000] input: USB HID v1.10 Mouse [Magic ball Mouse Magic ball Mouse] on usb-0000:02:09.0-2
```

Before the game break I had (NFL), I experienced a couple of moments when the mouse apparently disconnected and reconnected in a few moments. Then in a third moment, it simply stopped working. After the break (MARK MARK MARK etc) you may see the log about plugging the mouse back in another USB port (it seems that I can plug it back in successfully only once by using port 3 or 4 - if I were using port 1 or 2 before - but after disconnecting from ports 3/4 even unplugging-plugging back doesn't work).

---

### Post by Stefano Baghino on 2007-11-11
After a few minutes, as usual, the mouse stopped working again. Here are some more interesting logs...

/var/log/daemon.log

```
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.570197] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.720515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.820304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_usbraw'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.863102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0_logicaldev_input'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.586361] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0_logicaldev_input'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.588776] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.603441] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.610192] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_usbraw'). 
```

/var/log/debug

```
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.570197] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.720515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.820304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_usbraw'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.863102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0_logicaldev_input'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.586361] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0_logicaldev_input'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.588776] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.603441] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.610192] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_usbraw'). 
```

/var/log/kern.log

```
Nov 11 22:09:33 mark kernel: [14901.476000] usb 3-2: new low speed USB device using uhci_hcd and address 2
Nov 11 22:09:33 mark kernel: [14901.652000] usb 3-2: configuration #1 chosen from 1 choice
Nov 11 22:09:33 mark kernel: [14901.680000] input: Magic ball Mouse Magic ball Mouse as /class/input/input11
Nov 11 22:09:33 mark kernel: [14901.680000] input: USB HID v1.10 Mouse [Magic ball Mouse Magic ball Mouse] on usb-0000:02:09.0-2
Nov 11 22:26:12 mark kernel: [15900.452000] usb 3-2: USB disconnect, address 2
Nov 11 22:26:13 mark kernel: [15901.312000] usb 3-2: new low speed USB device using uhci_hcd and address 3
Nov 11 22:26:28 mark kernel: [15916.652000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:26:43 mark kernel: [15932.024000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:26:44 mark kernel: [15932.240000] usb 3-2: new low speed USB device using uhci_hcd and address 4
Nov 11 22:26:59 mark kernel: [15947.648000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:27:14 mark kernel: [15963.020000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:27:15 mark kernel: [15963.236000] usb 3-2: new low speed USB device using uhci_hcd and address 5
Nov 11 22:27:25 mark kernel: [15973.948000] usb 3-2: device not accepting address 5, error -110
Nov 11 22:27:25 mark kernel: [15974.060000] usb 3-2: new low speed USB device using uhci_hcd and address 6
Nov 11 22:27:36 mark kernel: [15984.784000] usb 3-2: device not accepting address 6, error -110
Nov 11 22:27:38 mark kernel: [15986.792000] usb usb3: Controller not stopped yet!
```

/var/log/syslog

```
Nov 11 22:09:33 mark kernel: [14901.476000] usb 3-2: new low speed USB device using uhci_hcd and address 2
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.570197] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial'). 
Nov 11 22:09:33 mark kernel: [14901.652000] usb 3-2: configuration #1 chosen from 1 choice
Nov 11 22:09:33 mark kernel: [14901.680000] input: Magic ball Mouse Magic ball Mouse as /class/input/input11
Nov 11 22:09:33 mark kernel: [14901.680000] input: USB HID v1.10 Mouse [Magic ball Mouse Magic ball Mouse] on usb-0000:02:09.0-2
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.720515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.820304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_usbraw'). 
Nov 11 22:09:33 mark NetworkManager: <debug> [1194815373.863102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0_logicaldev_input'). 
Nov 11 22:17:01 mark /USR/SBIN/CRON[14085]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 22:26:12 mark kernel: [15900.452000] usb 3-2: USB disconnect, address 2
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.586361] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0_logicaldev_input'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.588776] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_if0'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.603441] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial'). 
Nov 11 22:26:12 mark NetworkManager: <debug> [1194816372.610192] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_aef6_noserial_usbraw'). 
Nov 11 22:26:13 mark kernel: [15901.312000] usb 3-2: new low speed USB device using uhci_hcd and address 3
Nov 11 22:26:28 mark kernel: [15916.652000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:26:43 mark kernel: [15932.024000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:26:44 mark kernel: [15932.240000] usb 3-2: new low speed USB device using uhci_hcd and address 4
Nov 11 22:26:59 mark kernel: [15947.648000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:27:14 mark kernel: [15963.020000] usb 3-2: device descriptor read/64, error -110
Nov 11 22:27:15 mark kernel: [15963.236000] usb 3-2: new low speed USB device using uhci_hcd and address 5
Nov 11 22:27:25 mark kernel: [15973.948000] usb 3-2: device not accepting address 5, error -110
Nov 11 22:27:25 mark kernel: [15974.060000] usb 3-2: new low speed USB device using uhci_hcd and address 6
Nov 11 22:27:36 mark kernel: [15984.784000] usb 3-2: device not accepting address 6, error -110
Nov 11 22:27:38 mark kernel: [15986.792000] usb usb3: Controller not stopped yet!
```

Honestly I don't know much about log reading, but I'll try to look up some useful info. Meanwhile, any help is appreciated!

[CENTER]:confused:[/CENTER]

---

### Post by Stefano Baghino on 2007-11-12
I tried reinstalling Windows on the old hard disk but the problem with USB was right there expecting me, so the HDD's not the problem.

---

