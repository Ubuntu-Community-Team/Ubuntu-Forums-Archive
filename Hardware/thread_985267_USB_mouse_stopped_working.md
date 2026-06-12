---
title: "USB mouse stopped working"
date: 2008-11-17
forum: Hardware
---

### Post by mgangav on 2008-11-17
hello,

For some reason, my Microsoft Usb Optical mouse has decied to die out on me today. There is not that I am able to do that gets it working again. Here is what dmesg had to say about this:

```

[  102.994823] wlan0: associated
[  125.084096] usb 4-1: new low speed USB device using uhci_hcd and address 2
[  125.268772] usb 4-1: configuration #1 chosen from 1 choice
[  125.423582] usbcore: registered new interface driver hiddev
[  125.437660] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input11
[  125.444255] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.3-1
[  125.444301] usbcore: registered new interface driver usbhid
[  125.444308] usbhid: v2.6:USB HID core driver
[  131.344160] usb 4-1: USB disconnect, address 2
[  162.341065] ACPI: EC: missing confirmations, switch off interrupt mode.
[  162.860229] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[  162.860259] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.TZ00._TMP] (Node f7414000), AE_TIME
[  224.488750] usb 4-1: new low speed USB device using uhci_hcd and address 3
[  224.669992] usb 4-1: configuration #1 chosen from 1 choice
[  224.693770] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input12
[  224.728236] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.3-1
[  480.560066] NET: Registered protocol family 10
[  480.560983] lo: Disabled Privacy Extensions
[  480.562796] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  491.392078] wlan0: no IPv6 routers present
[  575.912142] usb 4-1: reset low speed USB device using uhci_hcd and address 3
[  576.180101] usb 4-1: device descriptor read/64, error -71
[  576.556098] usb 4-1: device descriptor read/64, error -71
[  576.920151] usb 4-1: reset low speed USB device using uhci_hcd and address 3
[  577.192098] usb 4-1: device descriptor read/64, error -71
[  577.564197] usb 4-1: device descriptor read/64, error -71
[  577.928162] usb 4-1: reset low speed USB device using uhci_hcd and address 3
[  578.340069] usb 4-1: device not accepting address 3, error -71
[  578.600124] usb 4-1: reset low speed USB device using uhci_hcd and address 3
[  579.008101] usb 4-1: device not accepting address 3, error -71
[  579.008175] usb 4-1: USB disconnect, address 3


```

So, what is going on there? Any advice?

---

### Post by mgangav on 2008-11-17
Strange, this is what dmesg says after I disconnect the mouse. It thinks that the mouse is still there?:

```

[  109.040720] wlan0: associated
[  109.040726] wlan0: CTS protection enabled (BSSID=00:12:0e:62:cc:d9)
[  130.864798] usb 3-1: reset low speed USB device using uhci_hcd and address 5
[  131.132420] usb 3-1: device descriptor read/64, error -71
[  131.503842] usb 3-1: device descriptor read/64, error -71
[  131.663137] NET: Registered protocol family 10
[  131.663693] lo: Disabled Privacy Extensions
[  131.665590] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  131.867224] usb 3-1: reset low speed USB device using uhci_hcd and address 5
[  132.134818] usb 3-1: device descriptor read/64, error -71
[  132.510233] usb 3-1: device descriptor read/64, error -71
[  132.873601] usb 3-1: reset low speed USB device using uhci_hcd and address 5
[  133.288951] usb 3-1: device not accepting address 5, error -71
[  133.548545] usb 3-1: reset low speed USB device using uhci_hcd and address 5
[  133.959891] usb 3-1: device not accepting address 5, error -71
[  133.959960] usb 3-1: USB disconnect, address 5
[  134.115654] usb 3-1: new low speed USB device using uhci_hcd and address 6
[  134.248417] usb 3-1: device descriptor read/64, error -71
[  134.471105] usb 3-1: device descriptor read/64, error -71
[  134.686737] usb 3-1: new low speed USB device using uhci_hcd and address 7
[  134.806667] usb 3-1: device descriptor read/64, error -71
[  135.034202] usb 3-1: device descriptor read/64, error -71
[  135.250859] usb 3-1: new low speed USB device using uhci_hcd and address 8
[  135.665180] usb 3-1: device not accepting address 8, error -71
[  135.777017] usb 3-1: new low speed USB device using uhci_hcd and address 9
[  136.185794] usb 3-1: device not accepting address 9, error -71
[  141.803467] wlan0: no IPv6 routers present
[  179.719376] usb 3-1: new low speed USB device using uhci_hcd and address 10
[  179.843184] usb 3-1: device descriptor read/64, error -71
[  180.066833] usb 3-1: device descriptor read/64, error -71
[  180.283474] usb 3-1: new low speed USB device using uhci_hcd and address 11
[  180.407292] usb 3-1: device descriptor read/64, error -71
[  180.629951] usb 3-1: device descriptor read/64, error -71
[  180.845600] usb 3-1: new low speed USB device using uhci_hcd and address 12
[  181.252933] usb 3-1: device not accepting address 12, error -71
[  181.364763] usb 3-1: new low speed USB device using uhci_hcd and address 13
[  181.776114] usb 3-1: device not accepting address 13, error -71
[  509.980751] usb 3-1: new low speed USB device using uhci_hcd and address 14
[  510.160785] usb 3-1: configuration #1 chosen from 1 choice
[  510.178908] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input14
[  510.228506] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.2-1
[  520.291455] usb 3-1: reset low speed USB device using uhci_hcd and address 14
[  522.467995] usb 3-1: USB disconnect, address 14

```

Another issue is that while restarting, usually, it says that it has failed to stop some processes from running.

---

### Post by mgangav on 2008-11-17
bump?

---

### Post by Psychoscorpic on 2008-11-18
Mgangav is not alone. I have the same problem.
Started when I connected my Sony Ericsson K750 phone and used it to dial onto the Web. There were some connection issues, and (red herring alert) I'm beginning to think that all the USB connections were remapped (no USB device is now visible to the machine.)
Plugging in the phone cable starts the phone beeping as if it is reconnecting continuously.
USB mouse or Flash Drive just doesn't automount.

My dmesg output is very similar.

---

### Post by john.adam on 2008-11-18
Hi Buddies

I am also with you. I am facing a strange problem. When i write something in Microsoft word xp it turns into white color and i cannot see that. I changed the font color black and even changed almost all color one by one, but the problem still persist. After that i uninstalled my MS Office and installed it again, result, the problem is the same. I am wonder, what to do this stupid word. The other Office applications are working normally. Will anybody solve this problem and have ever faced like this stupid problem?


John

---

### Post by Psychoscorpic on 2008-11-18
Hi John.Adam

I presume you mean you have two problems: (1) USB Mouse stopped functioning, and (2) the Word one?

As for the Word one: Are you running MS Word in Ubuntu via Wine? If so - Why? I'd suggest you stick to they way things are built to be, and use OpenOffice. If you need to share the resulting documents, you can easily Save-As Word2007 etc.
As to why it's white on white - never seen that. (unless you've fiddled with your Theme and set it like that)

(In future, it is better to use a separate thread for different issues, so as not to muddy the waters. You'll also more easily find a solution somebody else already submitted in the correct category)

---

### Post by mgangav on 2008-11-19
Yeah, so now my mouse has started to mysteriously work again. There was nothing that I did specifically to make it work. The reason why I tried out my mouse today was that when I plugged in my flash drive, it worked as normal, so when I tried my mouse, it worked also. Here is my dmesg output now:

```

 pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2776.528156] pci 0000:00:02.0: setting latency timer to 64
[ 2776.529841] PM: resume devices took 3.516 seconds
[ 2776.529928] PM: Finishing wakeup.
[ 2776.529930] Restarting tasks ... done.
[ 2776.781643] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 2776.781678] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2776.781685] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 2776.781774] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 2776.785711] ehci_hcd 0000:00:1d.7: debug port 1
[ 2776.785722] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 2776.785740] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000
[ 2776.803451] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 2776.803840] usb usb1: configuration #1 chosen from 1 choice
[ 2776.803905] hub 1-0:1.0: USB hub found
[ 2776.803922] hub 1-0:1.0: 8 ports detected
[ 2777.021191] USB Universal Host Controller Interface driver v3.0
[ 2777.021270] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 2777.021283] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2777.021287] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 2777.021332] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 2777.021373] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[ 2777.021546] usb usb2: configuration #1 chosen from 1 choice
[ 2777.021584] hub 2-0:1.0: USB hub found
[ 2777.021595] hub 2-0:1.0: 2 ports detected
[ 2777.120052] usb 1-4: new high speed USB device using ehci_hcd and address 2
[ 2777.125270] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2777.125290] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2777.125295] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 2777.125333] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 2777.125375] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
[ 2777.125488] usb usb3: configuration #1 chosen from 1 choice
[ 2777.125526] hub 3-0:1.0: USB hub found
[ 2777.125535] hub 3-0:1.0: 2 ports detected
[ 2777.268484] usb 1-4: configuration #1 chosen from 1 choice
[ 2777.276648] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09b0)
[ 2777.281929] input: UVC Camera (046d:09b0) as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input13
[ 2777.333284] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2777.333304] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2777.333308] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 2777.333345] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 2777.333385] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
[ 2777.333503] usb usb4: configuration #1 chosen from 1 choice
[ 2777.333541] hub 4-0:1.0: USB hub found
[ 2777.333553] hub 4-0:1.0: 2 ports detected
[ 2777.437302] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[ 2777.437323] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2777.437330] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 2777.437367] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 2777.437405] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
[ 2777.437525] usb usb5: configuration #1 chosen from 1 choice
[ 2777.437565] hub 5-0:1.0: USB hub found
[ 2777.437575] hub 5-0:1.0: 2 ports detected
[ 2777.563102] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2777.606970] iwl3945 0000:05:00.0: enabling device (0000 -> 0002)
[ 2777.606990] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2777.607063] iwl3945 0000:05:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2777.607133] iwl3945 0000:05:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0100000)
[ 2777.607147] iwl3945 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2777.607168] iwl3945 0000:05:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100106)
[ 2777.712807] Registered led device: iwl-phy0:radio
[ 2777.713132] Registered led device: iwl-phy0:assoc
[ 2777.713348] Registered led device: iwl-phy0:RX
[ 2777.713555] Registered led device: iwl-phy0:TX
[ 2777.714559] wlan0: authenticate with AP 00:18:39:75:42:0e
[ 2777.748981] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2777.785481] wlan0: authenticate with AP 00:18:39:75:42:0e
[ 2777.787332] wlan0: authenticated
[ 2777.787340] wlan0: associate with AP 00:18:39:75:42:0e
[ 2777.789573] wlan0: RX AssocResp from 00:18:39:75:42:0e (capab=0x401 status=0 aid=2)
[ 2777.789580] wlan0: associated
[ 2777.789903] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2777.819328] wlan0: disassociating by local choice (reason=3)
[ 2788.444075] wlan0: no IPv6 routers present
[ 2792.564883] wlan0: associate with AP 00:18:39:75:42:0e
[ 2792.567254] wlan0: RX ReassocResp from 00:18:39:75:42:0e (capab=0x401 status=0 aid=2)
[ 2792.567265] wlan0: associated
[ 2792.577829] wlan0: authenticate with AP 00:12:0e:62:cc:d9
[ 2792.580315] wlan0: authenticate with AP 00:12:0e:62:cc:d9
[ 2792.580338] wlan0: authenticated
[ 2792.580344] wlan0: associate with AP 00:12:0e:62:cc:d9
[ 2792.587835] wlan0: RX AssocResp from 00:12:0e:62:cc:d9 (capab=0x411 status=0 aid=2)
[ 2792.587850] wlan0: associated
[ 2927.269047] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 2927.788094] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 2927.788125] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.BAT1._BST] (Node f7419a20), AE_TIME
[ 2927.788222] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[ 4969.044143] usb 5-1: new low speed USB device using uhci_hcd and address 2
[ 4969.228794] usb 5-1: configuration #1 chosen from 1 choice
[ 4969.246596] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input14
[ 4969.300182] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.3-1
[ 5070.259336] Inbound IN=wlan0 OUT= MAC=00:19:d2:c6:eb:37:00:18:3a:32:0f:f3:08:00 SRC=192.168.1.254 DST=192.168.1.96 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=29134 DF PROTO=TCP SPT=1685 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 

```

I would really appreciate it if a more experienced Linux user than myself could interpret these results. What does dmesg do exactly? What do those numbers at the beginning of every line mean?

---

### Post by mgangav on 2008-11-22
Yeah, what on earth. The mouse randomly died again. This is what dmesg said:

```

[11695.735677] wlan0: associated
[13061.556091] usb 5-1: reset low speed USB device using uhci_hcd and address 2
[13061.828097] usb 5-1: device descriptor read/64, error -71
[13062.204056] usb 5-1: device descriptor read/64, error -71
[13062.568083] usb 5-1: reset low speed USB device using uhci_hcd and address 2
[13062.836082] usb 5-1: device descriptor read/64, error -71
[13063.212069] usb 5-1: device descriptor read/64, error -71
[13063.576098] usb 5-1: reset low speed USB device using uhci_hcd and address 2
[13063.984071] usb 5-1: device not accepting address 2, error -71
[13064.244133] usb 5-1: reset low speed USB device using uhci_hcd and address 2
[13064.652069] usb 5-1: device not accepting address 2, error -71
[13064.652141] usb 5-1: USB disconnect, address 2

```

---

