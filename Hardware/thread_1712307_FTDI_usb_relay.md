---
title: "FTDI usb relay"
date: 2011-03-22
forum: Hardware
---

### Post by Reactor89 on 2011-03-22
Hi all,

I have a relay controlled by a micro-controller and communicated to with a usb to serial FTDI chipset.

When I hot plug disconnect and reconnect the usb connection to the system, the relay works.

This is what dmesg says during the reconnect:
```

[  548.248114] usb 3-2: USB disconnect, address 2
[  548.248468] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[  548.248552] ftdi_sio 3-2:1.0: device disconnected
[  551.368046] usb 3-2: new full speed USB device using uhci_hcd and address 3
[  551.566437] usb 3-2: configuration #1 chosen from 1 choice
[  551.574386] ftdi_sio 3-2:1.0: FTDI USB Serial Device converter detected
[  551.574476] usb 3-2: Detected FT232RL
[  551.574484] usb 3-2: Number of endpoints 2
[  551.574491] usb 3-2: Endpoint 1 MaxPacketSize 64
[  551.574498] usb 3-2: Endpoint 2 MaxPacketSize 64
[  551.574505] usb 3-2: Setting MaxPacketSize 64
[  551.575438] usb 3-2: FTDI USB Serial Device converter now attached to ttyUSB0

```

Yet the FTDI device doesn't initialize correctly on startup.

Without a physical disconnect and reconnect the relay won't except commands:
```
-bash: /dev/ttyUSB0: Device or resource busy
```

This is what dmesg says during startup:
```

[   13.713218] USB Serial support registered for generic
[   13.713314] usbserial: USB Serial Driver core
[   13.946678] type=1505 audit(1300773471.524:2):  operation="profile_load" pid=519 name="/sbin/dhclient3"                                    
[   13.947529] type=1505 audit(1300773471.524:3):  operation="profile_load" pid=519 name="/usr/lib/NetworkManager/nm-dhcp-client.action"      
[   13.948125] type=1505 audit(1300773471.529:4):  operation="profile_load" pid=519 name="/usr/lib/connman/scripts/dhclient-script"           
[   13.967371] [drm] Initialized drm 1.1.0 20060810
[   14.008518] USB Serial support registered for FTDI USB Serial Device                                                                       
[   14.008733] ftdi_sio 3-2:1.0: FTDI USB Serial Device converter detected                                                                    
[   14.008943] usb 3-2: Detected FT232RL                                                                                                      
[   14.008952] usb 3-2: Number of endpoints 2                                                                                                 
[   14.008960] usb 3-2: Endpoint 1 MaxPacketSize 64                                                                                           
[   14.008967] usb 3-2: Endpoint 2 MaxPacketSize 64                                                                                           
[   14.008974] usb 3-2: Setting MaxPacketSize 64                                                                                              
[   14.012449] usb 3-2: FTDI USB Serial Device converter now attached to ttyUSB0                                                              
[   14.012607] usbcore: registered new interface driver ftdi_sio                                                                              
[   14.012616] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver

```

I'm looking for a way to initialize the relay correctly without physically disconnecting and reconnecting the relay.

Thanks

Reactor89

---

### Post by estratos on 2011-09-29
Hi Reactor,

I'm having the same problem with a FTDI-based USB/serial converter:
[http://ubuntuforums.org/showthread.php?p=11297305#post11297305](http://ubuntuforums.org/showthread.php?p=11297305#post11297305)

---

