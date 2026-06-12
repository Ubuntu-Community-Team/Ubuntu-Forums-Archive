---
title: "USB hub fails/disables after a few minutes"
date: 2008-11-07
forum: Hardware
---

### Post by stephanvaningen on 2008-11-07
I have a rather generic USB hub which stops working a few minutes after it is attached, or after some other device is attached to it. I have a messages log dump here:
[LIST]
[*]**[COLOR="DarkGreen"]Green[/COLOR]** = start of hub operations
[*]**[COLOR="Red"]Red[/COLOR]** = failure of hub
[/LIST]
```
Nov  8 05:20:56 living-vib kernel: [   51.808022] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov  8 05:20:56 living-vib kernel: [   51.817333] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov  8 05:20:56 living-vib kernel: [   51.817364] [fglrx] Reserved FB block: Unshared offset:7ffc000, size:4000 
Nov  8 05:21:10 living-vib kernel: [   65.346415] hda-intel: Invalid position buffer, using LPIB read method instead.
[COLOR="DarkGreen"]Nov  8 **05:21:16** living-vib kernel: [   71.568052] usb 6-6: new high speed USB device using ehci_hcd and address 4
Nov  8 05:21:16 living-vib kernel: [   71.701635] usb 6-6: configuration #1 chosen from 1 choice
Nov  8 05:21:16 living-vib kernel: [   71.717411] hub 6-6:1.0: USB hub found
Nov  8 05:21:16 living-vib kernel: [   71.718623] hub 6-6:1.0: 3 ports detected[/COLOR]
Nov  8 05:21:25 living-vib kernel: [   80.732267] usb 6-6.3: new low speed USB device using ehci_hcd and address 5
Nov  8 05:21:25 living-vib kernel: [   80.844632] usb 6-6.3: configuration #1 chosen from 1 choice
Nov  8 05:21:25 living-vib kernel: [   80.849411] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.5/usb6/6-6/6-6.3/6-6.3:1.0/input/input6
Nov  8 05:21:25 living-vib kernel: [   80.888261] input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:13.5-6.3
Nov  8 05:21:34 living-vib kernel: [   89.596256] usb 6-6.2: new low speed USB device using ehci_hcd and address 6
Nov  8 05:21:34 living-vib kernel: [   89.714974] usb 6-6.2: configuration #1 chosen from 1 choice
Nov  8 05:21:34 living-vib kernel: [   89.720546] input: CHICONY USB NetVista Full Width Keyboard as /devices/pci0000:00/0000:00:13.5/usb6/6-6/6-6.2/6-6.2:1.0/input/input7
Nov  8 05:21:34 living-vib kernel: [   89.768346] input,hidraw3: USB HID v1.10 Keyboard [CHICONY USB NetVista Full Width Keyboard] on usb-0000:00:13.5-6.2
Nov  8 05:22:32 living-vib pulseaudio[6216]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  8 05:22:32 living-vib pulseaudio[6218]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  8 05:22:32 living-vib pulseaudio[6218]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  8 05:22:46 living-vib kernel: [  161.381206] UDF-fs: No VRS found
Nov  8 05:23:47 living-vib sudo: pam_sm_authenticate: Called 
Nov  8 05:23:47 living-vib sudo: pam_sm_authenticate: username = [stephan] 
Nov  8 05:23:47 living-vib sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Nov  8 05:23:47 living-vib sudo: Unable to read salt value from user's .ecryptfsrc file; using default 
Nov  8 05:24:09 living-vib kernel: [  244.199537] type=1503 audit(1226118249.307:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6522/net/" pid=6522 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.315978] type=1503 audit(1226118250.423:7): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6527/net/" pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316026] type=1503 audit(1226118250.427:8): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316034] type=1503 audit(1226118250.427:9): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316042] type=1503 audit(1226118250.427:10): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316050] type=1503 audit(1226118250.427:11): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316057] type=1503 audit(1226118250.427:12): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316073] type=1503 audit(1226118250.427:13): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316081] type=1503 audit(1226118250.427:14): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
Nov  8 05:24:10 living-vib kernel: [  245.316091] type=1503 audit(1226118250.427:15): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6527 profile="/usr/sbin/cupsd"
[COLOR="Red"]Nov  8 05:24:56 living-vib kernel: [  291.640456] usb 6-6: USB disconnect, address 4
Nov  8 05:24:56 living-vib kernel: [  291.640478] usb 6-6.2: USB disconnect, address 6
Nov  8 05:24:56 living-vib kernel: [  291.716915] usb 6-6.3: USB disconnect, address 5
Nov  8 05:24:57 living-vib kernel: [  292.017248] usb 6-4: reset high speed USB device using ehci_hcd and address 2
Nov  8 05:25:12 living-vib kernel: [  307.109119] usb 6-4: USB disconnect, address 2[/COLOR]
Nov  8 05:25:12 living-vib kernel: [  307.109139] sd 6:0:0:0: Device offlined - not ready after error recovery
Nov  8 05:25:13 living-vib kernel: [  308.708059] usb 2-1: new low speed USB device using ohci_hcd and address 3
Nov  8 05:25:14 living-vib kernel: [  308.897512] usb 2-1: configuration #1 chosen from 1 choice
Nov  8 05:25:14 living-vib kernel: [  308.921858] input: CHICONY USB NetVista Full Width Keyboard as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.0/input/input8
Nov  8 05:25:14 living-vib kernel: [  308.965326] input,hidraw2: USB HID v1.10 Keyboard [CHICONY USB NetVista Full Width Keyboard] on usb-0000:00:13.1-1
Nov  8 05:25:21 living-vib kernel: [  315.917211] usb 2-2: new low speed USB device using ohci_hcd and address 4
Nov  8 05:25:21 living-vib kernel: [  316.086749] usb 2-2: configuration #1 chosen from 1 choice
Nov  8 05:25:21 living-vib kernel: [  316.094717] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.0/input/input9
Nov  8 05:25:21 living-vib kernel: [  316.143693] input,hidraw3: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:13.1-2
```

---

