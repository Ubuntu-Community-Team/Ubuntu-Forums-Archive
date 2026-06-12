---
title: "PDA no longer syncs"
date: 2008-05-27
forum: Hardware
---

### Post by bluewhale on 2008-05-27
My Windows mobile 5 PDA has been syncing with XP running in a VMWare W/S session on top of 7.04 for months. It would always throw a Ubuntu error when connected then allow the connection to proceed. 

As of a week ago it stopped popping the message up as well as stopped allowing the sync to occur. 

I've been googling and reading trying to determine what occurred. 

I'm not certain that I see it under Ubuntu's device manager. However I do see many entries under syslog.  Below are the log entries for a disconnect and connect again :



May 27 08:47:44 PaulT kernel: [ 1635.930714] usb 5-1: USB disconnect, address 3
May 27 08:47:44 PaulT kernel: [ 1635.931166] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
May 27 08:47:44 PaulT kernel: [ 1635.931209] ipaq 5-1:1.0: device disconnected
May 27 08:47:44 PaulT NetworkManager: <debug> [1211903264.177517] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_serial_usb_0'). 
May 27 08:47:44 PaulT NetworkManager: <debug> [1211903264.181520] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
May 27 08:47:44 PaulT NetworkManager: <debug> [1211903264.182941] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_ce_01145735_9379_0160_8800_0050bf3f5173_usbraw'). 
May 27 08:47:44 PaulT NetworkManager: <debug> [1211903264.184380] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_ce_01145735_9379_0160_8800_0050bf3f5173'). 
May 27 08:49:34 PaulT kernel: [ 1746.600006] usb 5-1: new full speed USB device using uhci_hcd and address 4
May 27 08:49:35 PaulT kernel: [ 1746.798159] usb 5-1: configuration #1 chosen from 1 choice
May 27 08:49:35 PaulT kernel: [ 1746.801080] ipaq 5-1:1.0: PocketPC PDA converter detected
May 27 08:49:35 PaulT kernel: [ 1746.803461] usb 5-1: PocketPC PDA converter now attached to ttyUSB0
May 27 08:49:35 PaulT NetworkManager: <debug> [1211903375.113588] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_ce_01145735_9379_0160_8800_0050bf3f5173'). 
May 27 08:49:35 PaulT NetworkManager: <debug> [1211903375.165124] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
May 27 08:49:35 PaulT NetworkManager: <debug> [1211903375.172908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_serial_usb_0'). 
May 27 08:49:35 PaulT NetworkManager: <debug> [1211903375.174224] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_ce_01145735_9379_0160_8800_0050bf3f5173_usbraw'). 


( side Q: how can I set such text into it's own window in a message here? )


Does the fact that a Windows client is polling for this device possibly cause Ubuntu to not 'see' it? 

Any thoughts on how to troubleshoot the problem? 

Any way to 'refresh' or manually mount the device in Ubuntu? ( none of the posts I've read indicate how to refresh USB or a single USB device. )

Thanks

---

