---
title: "PocketPC and SynCE again"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by ubuntuuser on 2005-08-01
I have followed the steps on the SynCE homepage but I am still not able to sync my Dell Axim X30 wih my laptop. I have managed to create a connection between both (at least synce-serial-start tells me it's waiting for the device t connect).
But ```
tail -f /var/log/messages
```tells a different story. It seems like the device is constantly disconnecting and reconnecting. A little extract from the console output:
```

Aug  1 19:30:58 localhost kernel: PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Aug  1 19:30:58 localhost kernel: ipaq 2-1:1.0: device disconnected
**Aug  1 19:31:04 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 63**
Aug  1 19:31:04 localhost kernel: ipaq 2-1:1.0: PocketPC PDA converter detected
Aug  1 19:31:04 localhost kernel: usb 2-1: PocketPC PDA converter now attached to ttyUSB0
Aug  1 19:31:13 localhost usb.agent[22226]:      ipaq: already loaded
Aug  1 19:31:13 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Aug  1 19:31:13 localhost pppd[22279]: pppd 2.4.2 started by root, uid 0
**Aug  1 19:31:13 localhost synce-serial-abort: Killing process with PID 22279**
Aug  1 19:31:13 localhost pppd[22279]: Terminating on signal 15.
Aug  1 19:31:13 localhost pppd[22279]: Exit.
Aug  1 19:31:13 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Aug  1 19:31:13 localhost pppd[22305]: pppd 2.4.2 started by root, uid 0
Aug  1 19:31:13 localhost usb.agent[22226]:      synce: loaded successfully
Aug  1 19:31:13 localhost synce-serial-abort: Killing process with PID 22305
Aug  1 19:31:13 localhost pppd[22305]: Terminating on signal 15.
Aug  1 19:31:13 localhost pppd[22305]: Exit.
**Aug  1 19:31:16 localhost kernel: usb 2-1: USB disconnect, address 63**
Aug  1 19:31:16 localhost kernel: PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Aug  1 19:31:16 localhost kernel: ipaq 2-1:1.0: device disconnected
**Aug  1 19:31:22 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 64**
Aug  1 19:31:22 localhost kernel: ipaq 2-1:1.0: PocketPC PDA converter detected
Aug  1 19:31:22 localhost kernel: usb 2-1: PocketPC PDA converter now attached to ttyUSB0
Aug  1 19:31:31 localhost usb.agent[22453]:      ipaq: already loaded
Aug  1 19:31:31 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Aug  1 19:31:31 localhost pppd[22506]: pppd 2.4.2 started by root, uid 0
**Aug  1 19:31:31 localhost synce-serial-abort: Killing process with PID 22506**
Aug  1 19:31:31 localhost pppd[22506]: Terminating on signal 15.
Aug  1 19:31:31 localhost pppd[22506]: Exit.
Aug  1 19:31:31 localhost usb.agent[22453]:      synce: loaded successfully
**Aug  1 19:31:34 localhost kernel: usb 2-1: USB disconnect, address 64**
Aug  1 19:31:34 localhost kernel: PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Aug  1 19:31:34 localhost kernel: ipaq 2-1:1.0: device disconnected
**Aug  1 19:31:40 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 65**
Aug  1 19:31:40 localhost kernel: ipaq 2-1:1.0: PocketPC PDA converter detected
Aug  1 19:31:40 localhost kernel: usb 2-1: PocketPC PDA converter now attached to ttyUSB0
Aug  1 19:31:49 localhost usb.agent[22664]:      ipaq: already loaded
Aug  1 19:31:49 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Aug  1 19:31:49 localhost synce-serial-abort: Killing process with PID 22717
Aug  1 19:31:49 localhost usb.agent[22664]:      synce: loaded successfully
Aug  1 19:31:49 localhost synce-serial-abort: Killing process with PID 22717
**Aug  1 19:31:52 localhost kernel: usb 2-1: USB disconnect, address 65**
Aug  1 19:31:52 localhost kernel: PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Aug  1 19:31:52 localhost kernel: ipaq 2-1:1.0: device disconnected
```

How can I keep the connection and prevent the dis-/reconnections?

---

### Post by ubuntuuser on 2005-08-04
*bump*

---

### Post by Vorik on 2005-08-12
This connecting and disconnecting behavioure was fixed on my system after fixing the "we're stuffed bug".

See [http://synce.sourceforge.net/synce/usb_linux.php](http://synce.sourceforge.net/synce/usb_linux.php)

Good luck!

Vorik.

---

