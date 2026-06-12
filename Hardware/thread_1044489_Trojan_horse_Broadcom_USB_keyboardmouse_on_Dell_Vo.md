---
title: "Trojan horse Broadcom USB keyboard/mouse on Dell Vostro 1500?"
date: 2009-01-19
forum: Hardware
---

### Post by seizurebattlerobot on 2009-01-19
Hello all!

While examining the output of dmesg on my Dell Vostro 1500 laptop the other day, I noticed something strange.  Toggling the onboard wireless kill-switch attaches and detaches two mysterious USB devices (in addition to the Intel wireless card it is supposed to control) -- a Broadcom mouse and keyboard.  Here's the log output produced by turning the kill-switch off (ie, enabling wireless):

```

[330162.316217] usb 1-2: new full speed USB device using uhci_hcd and address 117
[330162.499464] usb 1-2: configuration #1 chosen from 1 choice
[330162.505366] hub 1-2:1.0: USB hub found
[330162.507225] hub 1-2:1.0: 3 ports detected
[330162.802326] usb 1-2.1: new full speed USB device using uhci_hcd and address 118
[330162.936490] usb 1-2.1: configuration #1 chosen from 1 choice
[330163.032203] usb 1-2.2: new full speed USB device using uhci_hcd and address 119
[330163.179900] usb 1-2.2: configuration #1 chosen from 1 choice
[330163.187908] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input75
[330163.216334] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[330163.301212] usb 1-2.3: new full speed USB device using uhci_hcd and address 120
[330163.460834] usb 1-2.3: configuration #1 chosen from 1 choice
[330163.476906] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input76
[330163.534122] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[330166.974318] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[330166.974516] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[330167.020801] Registered led device: iwl-phy0:radio
[330167.022241] Registered led device: iwl-phy0:assoc
[330167.023605] Registered led device: iwl-phy0:RX
[330167.028154] Registered led device: iwl-phy0:TX

```

When I turn the kill switch on (ie, disable wireless), the two devices (and wireless card) are removed.  Here's the log:

```

[330124.113313] usb 1-2: USB disconnect, address 113
[330124.113326] usb 1-2.1: USB disconnect, address 114
[330124.113574] btusb_intr_complete: hci0 urb ffff8800915ec480 failed to resubmit (19)
[330124.119974] btusb_send_frame: hci0 urb ffff880046806480 submission failed
[330124.374383] usb 1-2.2: USB disconnect, address 115
[330124.468358] usb 1-2.3: USB disconnect, address 116

```

The driver for the mouse is automatically loaded.  It shows up in /dev/input as mouse1 for me.  I'm not exactly sure where the USB keyboard device would be listed.  Here's a before and after ls -l of /dev/input:

Before wireless is enabled:
```

total 0
drwxr-xr-x 2 root root    120 2009-01-19 12:35 by-path
crw-rw---- 1 root root 13, 64 2009-01-10 15:54 event0
crw-rw---- 1 root root 13, 65 2009-01-10 15:54 event1
crw-rw---- 1 root root 13, 74 2009-01-10 15:54 event10
crw-rw---- 1 root root 13, 67 2009-01-10 15:54 event3
crw-rw---- 1 root root 13, 68 2009-01-10 15:54 event4
crw-rw---- 1 root root 13, 69 2009-01-10 15:54 event5
crw-rw---- 1 root root 13, 70 2009-01-10 15:54 event6
crw-rw---- 1 root root 13, 71 2009-01-10 15:54 event7
crw-rw---- 1 root root 13, 72 2009-01-10 15:54 event8
crw-rw---- 1 root root 13, 73 2009-01-10 15:54 event9
crw-rw---- 1 root root 13, 63 2009-01-10 15:53 mice
crw-rw---- 1 root root 13, 32 2009-01-10 15:53 mouse0
crw-rw---- 1 root root 13, 34 2009-01-10 15:54 mouse2

```

After wireless is enabled:
```

total 0
drwxr-xr-x 2 root root    100 2009-01-19 12:33 by-id
drwxr-xr-x 2 root root    180 2009-01-19 12:33 by-path
crw-rw---- 1 root root 13, 64 2009-01-10 15:54 event0
crw-rw---- 1 root root 13, 65 2009-01-10 15:54 event1
crw-rw---- 1 root root 13, 74 2009-01-10 15:54 event10
crw-rw---- 1 root root 13, 75 2009-01-19 12:33 event11
crw-rw---- 1 root root 13, 66 2009-01-19 12:33 event2
crw-rw---- 1 root root 13, 67 2009-01-10 15:54 event3
crw-rw---- 1 root root 13, 68 2009-01-10 15:54 event4
crw-rw---- 1 root root 13, 69 2009-01-10 15:54 event5
crw-rw---- 1 root root 13, 70 2009-01-10 15:54 event6
crw-rw---- 1 root root 13, 71 2009-01-10 15:54 event7
crw-rw---- 1 root root 13, 72 2009-01-10 15:54 event8
crw-rw---- 1 root root 13, 73 2009-01-10 15:54 event9
crw-rw---- 1 root root 13, 63 2009-01-10 15:53 mice
crw-rw---- 1 root root 13, 32 2009-01-10 15:53 mouse0
crw-rw---- 1 root root 13, 33 2009-01-19 12:33 mouse1
crw-rw---- 1 root root 13, 34 2009-01-10 15:54 mouse2

```

The big question is, what is the purpose of these Broadcom USB devices?  I realize that calling these devices Trojan horses is a pretty serious allegation, but I cannot think of any other explanation.  So, what have I overlooked?

Does anyone here know of another explanation for what these devices might be?  I'll be happy to provide logs and other information to anybody curious enough to help me figure this one out.

---

