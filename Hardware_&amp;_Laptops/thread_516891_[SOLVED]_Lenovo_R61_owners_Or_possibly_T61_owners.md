---
title: "[SOLVED] Lenovo R61 owners? Or possibly T61 owners?"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by smbm on 2007-08-03
Hi 

I've just purchased this superb laptop (R61) and have been working for a couple of days now to get everything set up just right. I think I've nearly succeeded, got hdaps, hotkeys, wifi, sound and video all working swimmingly, even the finger print reader is working just how I want.

One thing I haven't managed to sort out though is hot pluggable/automounting USB drives.

Does anyone else who owns one of these laptops have any problems with their USB ports? Does anyone know of any fixes? Or even how I can begin to find out what the problem is?

The devices are recognized but not automounted.

Cheers in advance.

P.s I think this problem applies to T61s too.

P.p.s If anyone needs help with almost any other piece of hardware on this baby give me a shout and I'll be happy to share what I know.

---

### Post by Darrena on 2007-08-04
> **smbm said:**
> Hi 

I've just purchased this superb laptop (R61) and have been working for a couple of days now to get everything set up just right. I think I've nearly succeeded, got hdaps, hotkeys, wifi, sound and video all working swimmingly, even the finger print reader is working just how I want.

One thing I haven't managed to sort out though is hot pluggable/automounting USB drives.

Does anyone else who owns one of these laptops have any problems with their USB ports? Does anyone know of any fixes? Or even how I can begin to find out what the problem is?

The devices are recognized but not automounted.

Cheers in advance.

P.s I think this problem applies to T61s too.

P.p.s If anyone needs help with almost any other piece of hardware on this baby give me a shout and I'll be happy to share what I know.

I have had no problems with mounting USB drives.  If you tail /var/log/messages or /var/log/syslog when you plug in the drive do you see any errors?

tail -f /var/log/syslog
tail -f /var/log/messages

Also do you have a Intel video or Nvidia?

---

### Post by smbm on 2007-08-04
Hi

Thanks for replying.

I'm using Intel graphics.

I should probably take this moment to tell you I'm using Gutsy, my desktop that's running Gutsy automounts fine though.

Ok, so I plugged in my iPod and here is the output from those 2 logs:

/var/log/syslog

```
Aug  4 23:11:30 localhost NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Aug  4 23:12:20 localhost kernel: [ 7598.168000] usb 6-3: new high speed USB device using ehci_hcd and address 7
Aug  4 23:12:20 localhost kernel: [ 7598.300000] usb 6-3: configuration #1 chosen from 2 choices
Aug  4 23:12:20 localhost kernel: [ 7598.300000] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  4 23:12:20 localhost kernel: [ 7598.300000] usb-storage: device found at 7
Aug  4 23:12:20 localhost kernel: [ 7598.300000] usb-storage: waiting for device to settle before scanning
Aug  4 23:12:20 localhost NetworkManager: <debug> [1186265540.913608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001596B94B'). 
Aug  4 23:12:20 localhost NetworkManager: <debug> [1186265540.952097] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001596B94B_if0'). 
Aug  4 23:12:20 localhost NetworkManager: <debug> [1186265540.963122] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001596B94B_usbraw'). 
Aug  4 23:12:25 localhost kernel: [ 7603.300000] usb-storage: device scan complete
Aug  4 23:12:25 localhost kernel: [ 7603.300000] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Aug  4 23:12:25 localhost kernel: [ 7603.300000] sd 5:0:0:0: [sdc] 58605120 512-byte hardware sectors (30006 MB)
Aug  4 23:12:25 localhost kernel: [ 7603.300000] sd 5:0:0:0: [sdc] Write Protect is off
Aug  4 23:12:25 localhost kernel: [ 7603.300000] sd 5:0:0:0: [sdc] Mode Sense: 6c 00 00 08
Aug  4 23:12:25 localhost kernel: [ 7603.300000] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug  4 23:12:25 localhost kernel: [ 7603.304000] sd 5:0:0:0: [sdc] 58605120 512-byte hardware sectors (30006 MB)
Aug  4 23:12:25 localhost kernel: [ 7603.304000] sd 5:0:0:0: [sdc] Write Protect is off
Aug  4 23:12:25 localhost kernel: [ 7603.304000] sd 5:0:0:0: [sdc] Mode Sense: 6c 00 00 08
Aug  4 23:12:25 localhost kernel: [ 7603.304000] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug  4 23:12:25 localhost kernel: [ 7603.304000]  sdc: sdc1 sdc2
Aug  4 23:12:25 localhost kernel: [ 7603.320000] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Aug  4 23:12:25 localhost kernel: [ 7603.320000] sd 5:0:0:0: Attached scsi generic sg2 type 0
Aug  4 23:12:26 localhost NetworkManager: <debug> [1186265546.025368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001596B94B_if0_scsi_host'). 
Aug  4 23:12:26 localhost NetworkManager: <debug> [1186265546.028616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001596B94B_if0_scsi_host_scsi_device_lun0'). 
Aug  4 23:12:26 localhost NetworkManager: <debug> [1186265546.034715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001596B94B_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug  4 23:12:26 localhost NetworkManager: <debug> [1186265546.141097] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001596B94B_0_0'). 
Aug  4 23:12:26 localhost NetworkManager: <debug> [1186265546.340508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_82220544'). 
Aug  4 23:12:26 localhost NetworkManager: <debug> [1186265546.386627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_0071_6022'). 

```

/var/log/messages

```
Aug  4 23:09:33 localhost kernel: [ 7430.536000] Kill switch must be turned off for wireless networking to work.
Aug  4 23:12:20 localhost kernel: [ 7598.168000] usb 6-3: new high speed USB device using ehci_hcd and address 7
Aug  4 23:12:20 localhost kernel: [ 7598.300000] usb 6-3: configuration #1 chosen from 2 choices
Aug  4 23:12:20 localhost kernel: [ 7598.300000] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  4 23:12:25 localhost kernel: [ 7603.300000] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Aug  4 23:12:25 localhost kernel: [ 7603.300000] sd 5:0:0:0: [sdc] 58605120 512-byte hardware sectors (30006 MB)
Aug  4 23:12:25 localhost kernel: [ 7603.300000] sd 5:0:0:0: [sdc] Write Protect is off
Aug  4 23:12:25 localhost kernel: [ 7603.304000] sd 5:0:0:0: [sdc] 58605120 512-byte hardware sectors (30006 MB)
Aug  4 23:12:25 localhost kernel: [ 7603.304000] sd 5:0:0:0: [sdc] Write Protect is off
Aug  4 23:12:25 localhost kernel: [ 7603.304000]  sdc: sdc1 sdc2
Aug  4 23:12:25 localhost kernel: [ 7603.320000] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Aug  4 23:12:25 localhost kernel: [ 7603.320000] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

There didn't seem to be any glaring errors in that. Not that I could spot anyway.

Any advice would be awesome.

Cheers

---

### Post by era86 on 2007-08-05
What kind of Wireless do you have?  I might get a T61 and I don't know if I should pay the extra $45 to get the Intel Wireless.  Does the Thinkpad a/g/b wireless work?

---

### Post by smbm on 2007-08-05
I've got Intel wireless but haven't had an occasion to give it a really hardcore test it yet. I've tried it a couple of times and it seems to work.

---

### Post by Darrena on 2007-08-05
Very odd...   I would recommend taking a look at this wiki page:

[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

---

### Post by smbm on 2007-08-05
The weird thing is; it seems to work fine with the live cd. I guess it could be a Gutsy problem. I'll check the link out though, thanks.

---

### Post by era86 on 2007-08-06
I'll be a proud owner of a new T61 by next week.  Putting the order in today.  Hopefully things work out.

---

### Post by smbm on 2007-08-11
This seems to have been fixed lately so I'm going to mark it solved.

---

