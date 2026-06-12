---
title: "USB mouse / keyboard jerky after few minutes"
date: 2008-05-30
forum: Hardware
---

### Post by jonface on 2008-05-30
I've just updated (clean) to 8.04 from 7.10 and having some problems with mouse and keyboard.

Both mouse and keyboard worked fine under 7.10 and are plugged directly into the laptop. After a few minutes, they become jerky and I noticed this via dmesg,

```
[  393.149523] usb 5-4: new high speed USB device using ehci_hcd and address 10
[  400.313663] usb 5-4: device not accepting address 10, error -110
[  400.365241] usb 5-4: new high speed USB device using ehci_hcd and address 11
[  407.529381] usb 5-4: device not accepting address 11, error -110
[  407.580959] usb 5-4: new high speed USB device using ehci_hcd and address 12
[  412.385306] usb 5-4: device not accepting address 12, error -110
[  412.436879] usb 5-4: new high speed USB device using ehci_hcd and address 13
[  417.241218] usb 5-4: device not accepting address 13, error -110
```

lsusb
```

Bus 004 Device 003: ID 0db0:a970 Micro Star International Bluetooth dongle
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 07c4:3260 Datafab Systems, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID eb1a:2750 eMPIA Technology, Inc. ECS Elitegroup G220 integrated webcam
Bus 001 Device 004: ID 045e:00b0 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  


```


I guess this is something to do with it? I read somewhere else some problem with ehci_hcd so I tried removing it but still the same thing.

```
[  552.019683] ehci_hcd 0000:00:10.4: remove, state 1
[  552.019692] usb usb5: USB disconnect, address 1
[  552.019694] usb 5-2: USB disconnect, address 6
[  552.020127] ehci_hcd 0000:00:10.4: USB bus 5 deregistered
[  552.020163] ACPI: PCI interrupt for device 0000:00:10.4 disabled
[  552.194247] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  552.769082] usb 1-2: configuration #1 chosen from 1 choice
[  554.596441] usb 3-1: USB disconnect, address 3
[  562.770065] usb 3-1: new low speed USB device using uhci_hcd and address 4
[  564.190288] usb 3-1: configuration #1 chosen from 1 choice
[  564.533004] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.0/input/input13
[  564.544388] input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.2-1
[  564.672859] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  566.246141] usb 2-2: configuration #1 chosen from 1 choice
[  566.360922] scsi6 : SCSI emulation for USB Mass Storage devices
[  566.361019] usb-storage: device found at 2
[  566.361022] usb-storage: waiting for device to settle before scanning
[  568.758801] usb-storage: device scan complete
[  569.101596] scsi 6:0:0:0: Direct-Access     GENERIC  USB Storage-CFC  019A PQ: 0 ANSI: 0 CCS
[  569.444230] scsi 6:0:0:1: Direct-Access     GENERIC  USB Storage-SDC  019A PQ: 0 ANSI: 0 CCS
[  569.786873] scsi 6:0:0:2: Direct-Access     GENERIC  USB Storage-SMC  019A PQ: 0 ANSI: 0 CCS
[  570.129510] scsi 6:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  019A PQ: 0 ANSI: 0 CCS
[  570.701072] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  570.701104] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  571.272148] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[  571.272180] sd 6:0:0:1: Attached scsi generic sg4 type 0
[  572.414262] sd 6:0:0:2: [sde] Attached SCSI removable disk
[  572.414290] sd 6:0:0:2: Attached scsi generic sg5 type 0
[  574.127121] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[  574.127150] sd 6:0:0:3: Attached scsi generic sg6 type 0

```

xorg.conf mouse section. Worked fine under 7.10. Have also tried removing the options (this was the default). No luck.
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

I tried unplugging the mouse and plugging it back in but it just dies then and won't come back. Confused. The keyboard and touchpad on the laptop work fine, just USB seems to be all over the place. Looking at dmesg the built in memory card reader seems to be up to something as well sdc,sdd,sde,sdf.

So, what's changed from 7.10 to 8.04?

If this is a repeat of another post I did try and check first but didn't find anything.

Thanks,

---

### Post by xpelaox on 2008-05-31
Hey, I Have a similar/related problem, in the other thread you posted, if you don't mind, i'm gonna copy it here, may be it can hel sombody to fix our problems.

> Hi guys! This is my first post here, Hope you can help me!I tried to search, but couldn't find nothing even similar to my problem:S

First of all, Sorry for my english

I've got a Hp Tx1030LA(tx1000 series) notebook, with ubuntu 8.04, i could manage to set up almost everything, but i've got a VERY annoying problem.

I boot ubuntu with "noacpi" in that way, everything seems to work fine, the problem comes into scene when the notebook is inactive for a while, when the screen goes black, i move the mouse, but after that, the mouse and keyboard begin to lag and it is virtualy impossible to use! i belive the problem is related to noacpi or some energy saving stuff. i tried to set the computer in order to be ALWAYS ACTIVE, no black screen, no nothing, but after a while the problem appears.

I forgot to mention above an important part of this "Story" I am using an xb3000 docking station, which seems to work fine. but I belive it is worth mentioning.

and well.... thats the whole thing... hope you can help me guys, i really wanna live a Windows-Free life!

Thanks you and sorry for my english again.

---

### Post by jonface on 2008-06-08
Gone back to 7.10, needed to do work. Would still be interested in a fix though.

---

### Post by xpelaox on 2008-06-09
but it works in 7.10?? i've got the same problem in 7.10 and 8.04.

installed debian and when the problem appears this mensage appears in consnole: Disabling IRQ #7

but it doesn't seem to have any solution... must i say, Hello again vista?:S:(

---

