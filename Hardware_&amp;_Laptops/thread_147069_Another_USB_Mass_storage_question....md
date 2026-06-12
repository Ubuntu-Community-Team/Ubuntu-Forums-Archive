---
title: "Another USB Mass storage question..."
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by Sophisto on 2006-03-19
Hello everyone! After reading several posts about other flashdisk related problem I still cant figure out how to mount my camera flash disk... here are some outputs

```
akerstrom@c-637ee455:/mnt$ tail -f /var/log/messages
Mar 19 20:56:17 localhost kernel: [4296766.393000] usb 3-1.1: USB disconnect, address 4
Mar 19 20:56:24 localhost kernel: [4296773.003000] atkbd.c: Unknown key released (translated set 2, c ode 0xaa on isa0060/serio0).
Mar 19 20:56:24 localhost kernel: [4296773.003000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Mar 19 20:56:24 localhost kernel: [4296773.101000] atkbd.c: Unknown key pressed (translated set 2, co de 0xaa on isa0060/serio0).
Mar 19 20:56:24 localhost kernel: [4296773.101000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Mar 19 20:56:53 localhost kernel: [4296802.247000] usb 3-1.2: new full speed USB device using ohci_hc d and address 5
Mar 19 20:56:53 localhost kernel: [4296802.325000] scsi2 : SCSI emulation for USB Mass Storage device s
Mar 19 20:56:53 localhost usb.agent[9580]:      usb-storage: already loaded
Mar 19 20:56:59 localhost kernel: [4296807.917000]   Vendor:           Model:                   Rev: 
Mar 19 20:56:59 localhost kernel: [4296807.917000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar 19 20:57:12 localhost scsi.agent[9631]: Attribute /sys/devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1.2/3-1.2:1.0/host2/ target2:0:0/2:0:0:0/type does not exist
Mar 19 20:57:30 localhost kernel: [4296838.954000] sda: test WP failed, assume Write Enabled
Mar 19 20:57:30 localhost kernel: [4296838.956000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Mar 19 20:58:32 localhost kernel: [4296900.999000] sda: test WP failed, assume Write Enabled

```

```
akerstrom@c-637ee455:/mnt$ lsusb
Bus 004 Device 002: ID 03f0:2b17 Hewlett-Packard
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 005: ID 04e6:0006 SCM Microsystems, Inc. eUSB SmartMedia Card Reader
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0009 Microsoft Corp. IntelliMouse
Bus 001 Device 001: ID 0000:0000

```

Extracts from dmesg
```
[4295188.976000] usb 3-1.4: USB disconnect, address 3
[4295192.859000] usb 3-1.1: new full speed USB device using ohci_hcd and address 4
[4295192.937000] scsi1 : SCSI emulation for USB Mass Storage devices
[4295192.941000] usb-storage: device found at 4
[4295192.941000] usb-storage: waiting for device to settle before scanning
[4295198.530000]   Vendor:           Model:                   Rev:
[4295198.530000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4295229.569000] sda: test WP failed, assume Write Enabled
[4295229.569000] sda: assuming drive cache: write through
[4295229.570000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[4295229.576000] usb-storage: device scan complete
[4295291.673000] sda: test WP failed, assume Write Enabled
[4295291.673000] sda: assuming drive cache: write through
[4295948.448000] sda: test WP failed, assume Write Enabled
[4295948.448000] sda: assuming drive cache: write through
[4296040.904000] sda: test WP failed, assume Write Enabled
[4296040.904000] sda: assuming drive cache: write through
[4296609.104000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296609.104000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296609.202000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296609.202000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296685.543000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296685.543000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296685.639000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296685.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296766.393000] usb 3-1.1: USB disconnect, address 4
[4296773.003000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296773.003000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296773.101000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296773.101000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296802.247000] usb 3-1.2: new full speed USB device using ohci_hcd and address 5
[4296802.325000] scsi2 : SCSI emulation for USB Mass Storage devices
[4296802.329000] usb-storage: device found at 5
[4296802.329000] usb-storage: waiting for device to settle before scanning
[4296807.917000]   Vendor:           Model:                   Rev:
[4296807.917000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4296838.954000] sda: test WP failed, assume Write Enabled
[4296838.954000] sda: assuming drive cache: write through
[4296838.956000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[4296838.962000] usb-storage: device scan complete
[4296900.999000] sda: test WP failed, assume Write Enabled
[4296900.999000] sda: assuming drive cache: write through
[4297243.153000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297243.153000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297243.254000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297243.254000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297288.312000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297288.312000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297288.395000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297288.395000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

I have tried to mount it with ```
sudo mount -t vfat /dev/sdxx /mnt/usb 
``` and have tried various combinations like sda1 to sda9 and also sdb1 to 9 etc.. no success... 

```
mount: special device /dev/sda2 does not exist

```

Any suggestions?

PS. And no, it doesnt appear on my desktop if anyone was wondering... 
DS

---

### Post by taurus on 2006-03-19
```

sudo mkdir /mnt/usb
sudo mount -t vfat /dev/sda /mnt/usb
df -h

```

---

### Post by Sophisto on 2006-03-19
I have already made a folder for my mount point...

---

### Post by ranf on 2006-03-21
Do you get something useful from:
```
fdisk -l /dev/sda
```

---

### Post by Sophisto on 2006-03-23
my shell freezes when executing the fdisk command... so yes im not sure whether Ill ever get this usb stick of mine to work...

---

### Post by ranf on 2006-03-24
That looks weird. I wish I had an idea how to help you.

---

### Post by Sophisto on 2006-04-02
Have just realised that the USB-memory was inserted upsidedown in the usb-socket... It was my parents PC + usb-memory so I never checked this... now it works... my bad.

---

