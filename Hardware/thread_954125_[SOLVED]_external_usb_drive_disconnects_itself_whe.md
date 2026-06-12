---
title: "[SOLVED] external usb drive disconnects itself when connecting"
date: 2008-10-20
forum: Hardware
---

### Post by diagonallemma on 2008-10-20
I'm trying to access an external USB drive (Western Digital, 160GB) from Ubuntu 8.04. Unfortunately, it doesn't show up when I plug it in, not even under fdisk -l. 

From the logs, it looks like the drive gets disconnected immediately after connecting. /var/log/syslog says:

```

Oct 21 12:30:54 wo-desktop NetworkManager: <debug> [1224552654.138257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_E511F0E392DC541457CCFDB4_if0'). 
Oct 21 12:30:54 wo-desktop NetworkManager: <debug> [1224552654.140864] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_E511F0E392DC541457CCFDB4_if0'). 
Oct 21 12:30:54 wo-desktop NetworkManager: <debug> [1224552654.140936] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_E511F0E392DC541457CCFDB4'). 
Oct 21 12:30:54 wo-desktop pulseaudio[6533]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_1058_702_E511F0E392DC541457CCFDB4_if0
```

Not sure what NetworkManager and PulseAudio have to do with USB handling.. Here is dmesg:

```
Oct 21 12:30:53 wo-desktop kernel: [14017.920885] usb 5-8: new high speed USB device using ehci_hcd and address 9
Oct 21 12:30:54 wo-desktop kernel: [14018.052783] usb 5-8: configuration #1 chosen from 1 choice
Oct 21 12:30:54 wo-desktop kernel: [14018.063463] scsi7 : SCSI emulation for USB Mass Storage devices
Oct 21 12:30:54 wo-desktop kernel: [14018.133089] usb 5-8: USB disconnect, address 9
```

Any help would be much appreciated.

---

### Post by diagonallemma on 2008-10-23
..tried a different cable and now it's working.

---

### Post by JC Cheloven on 2008-10-23
> **diagonallemma said:**
> ..tried a different cable and now it's working.

Great to hear this :-)

Could you please mark the thread as solved? Even these small things can help other people in the future.

---

