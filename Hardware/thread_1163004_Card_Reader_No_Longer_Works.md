---
title: "Card Reader No Longer Works"
date: 2009-05-18
forum: Hardware
---

### Post by fallenshadow on 2009-05-18
Please help! My card reader used to always work flawlessly and now it won't.

When I used lsusb in the terminal it was listed as:

ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

Is there any way to reconfigure it or something?

---

### Post by Lampi on 2009-05-18
Watch what udev is doing when you plug/unplug it

open terminal and type dmesg |tail -n50

this should show you what udev is trying to do with your card reader device

I'd expect some sort of error message you can follow upon, best is you google it first, then ask here.

It *should* show up as device in /dev/ if everything works fine, mine for example would be assigned as /dev/ttyUSB0 yours might be different.

---

### Post by fallenshadow on 2009-05-19
I can't find any error message relating to my memory card reader. Here is the output:

```
[   29.757869] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   29.772125] phy0: Selected rate control algorithm 'simple'
[   29.839481] usbcore: registered new interface driver rt73usb
[   29.839506] usbcore: registered new interface driver lirc_atiusb
[   29.839595] usbcore: registered new interface driver usb-storage
[   29.839598] USB Mass Storage support registered.
[   29.839922] usbcore: registered new interface driver snd-usb-audio
[   29.851598] usbcore: registered new interface driver rt2500usb
[   30.697240] lp0: using parport0 (interrupt-driven).
[   30.741532] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   31.279425] EXT3 FS on sda1, internal journal
[   32.379329] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.730981] No dock devices found.
[   33.766043] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   33.766049] apm: disabled - APM is not SMP safe.
[   33.868444] ppdev: user-space parallel port driver
[   34.048672] audit(1242721131.435:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5366 profile="/usr/sbin/cupsd" namespace="default"
[   34.577379] usb-storage: device scan complete
[   34.581500] scsi 4:0:0:0: Direct-Access     Generic  Flash HS-CF      4.44 PQ: 0 ANSI: 0
[   34.584870] scsi 4:0:0:1: Direct-Access     Generic  Flash HS-MS/SD   4.44 PQ: 0 ANSI: 0
[   34.588114] scsi 4:0:0:2: Direct-Access     Generic  Flash HS-SM      4.44 PQ: 0 ANSI: 0
[   34.598381] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   34.598425] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   34.649613] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   34.649659] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   34.654160] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   34.654199] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   36.526070] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   36.526075] vboxdrv: Successfully done.
[   36.526077] vboxdrv: Found 2 processor cores.
[   36.526131] vboxdrv: fAsync=0 offMin=0x2e6 offMax=0xc0f
[   36.526176] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   36.526179] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
[   38.677105] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.773640] Bluetooth: Core ver 2.11
[   38.773769] NET: Registered protocol family 31
[   38.773772] Bluetooth: HCI device and connection manager initialized
[   38.773777] Bluetooth: HCI socket layer initialized
[   38.786867] Bluetooth: L2CAP ver 2.9
[   38.786872] Bluetooth: L2CAP socket layer initialized
[   38.862367] Bluetooth: RFCOMM socket layer initialized
[   38.862386] Bluetooth: RFCOMM TTY layer initialized
[   38.862388] Bluetooth: RFCOMM ver 1.8
[   42.165462] NET: Registered protocol family 17
[   47.854874] NET: Registered protocol family 10
[   47.855168] lo: Disabled Privacy Extensions
[   47.856172] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.436057] hda-intel: Invalid position buffer, using LPIB read method instead.
[   58.545952] eth0: no IPv6 routers present
[  123.995428] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1289: 3:3:1: cannot set freq 16000 to ep 0x86

```

---

### Post by fallenshadow on 2009-06-08
Bump! Anyone have any ideas on how to fix this? Plz offer a suggestion if you have one! ;)

---

