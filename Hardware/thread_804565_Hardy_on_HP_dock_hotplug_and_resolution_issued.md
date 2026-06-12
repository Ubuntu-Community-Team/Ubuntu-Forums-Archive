---
title: "Hardy on HP dock hotplug and resolution issued"
date: 2008-05-23
forum: Hardware
---

### Post by Strelock on 2008-05-23
Hi all! I have some weired behavior with Hardy which I didn't have with Ubuntu 7.04...

To start with I'm using Compaq nw8440 laptop, dock station and two external screens connected to it. Before I could switch with *aticonfig --enable-monitor=* to any of the following:
1) *lmds* - laptop only  1920x1200
2) *lmds, tmds1* - laptop + dvi connected screen
3) *lmds, crt1* - laptop + vga connected screen
4) *tmds1, crt1* - dva and vga connected screens with 2560x1024

Now the issues are:
issuing *aticonfig --enable-monitor=lmds  --effective=now* when using **tmds1 and crt1** restart X.
Issuing: 
[I]aticonfig --enable-monitor=lmds,tmds1  --effective=now
aticonfig --enable-monitor=lmds  --effective=now[/I]
works out, the laptop screen is black, but icons and windows appear when active.

Going from laptop screen to any of the dual configs is just fine.

**More issues:**
1. Hot pluging / unplugging from dock would normally kill either X or the whole pc
2. After *rmmod dock* and */etc/init.d/atieventsd stop* hot docking / undocking is survaivable, but screen switching issue is still there...

Some more info:
**uname -r**
2.6.24-16-generic

**difference in dsmesg pre and post hotplug dock:**
[  105.301412] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  105.301420] tg3: eth0: Flow control is off for TX and off for RX.
[  105.305091] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  105.305164] iwl3945: Radio Frequency Kill Switch is On:
[  105.305166] Kill switch must be turned off for wireless networking to work.
[  105.414267] usb 5-8: new high speed USB device using ehci_hcd and address 3
[  105.549448] usb 5-8: configuration #1 chosen from 1 choice
[  105.549778] hub 5-8:1.0: USB hub found
[  105.550682] hub 5-8:1.0: 4 ports detected
[  105.856595] usb 5-8.3: new low speed USB device using ehci_hcd and address 4
[  106.718953] CPU0 attaching NULL sched-domain.
[  106.718957] CPU1 attaching NULL sched-domain.
[  106.755882] CPU0 attaching sched-domain:
[  106.755887]  domain 0: span 03
[  106.755888]   groups: 01 02
[  106.755891] CPU1 attaching sched-domain:
[  106.755893]  domain 0: span 03
[  106.755894]   groups: 02 01
[  115.739185] eth0: no IPv6 routers present
[  116.318177] usb 5-8.3: device not accepting address 4, error -110
[  116.390158] usb 5-8.3: new low speed USB device using ehci_hcd and address 5
[  131.435837] usb 5-8.3: device descriptor read/64, error -110
[  131.656623] usb 5-8.3: configuration #1 chosen from 1 choice
[  131.855193] usb 5-8.4: new low speed USB device using ehci_hcd and address 6
[  131.951258] usb 5-8.4: configuration #1 chosen from 1 choice
[  132.166398] usbcore: registered new interface driver hiddev
[  132.176081] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8.3/5-8.3:1.0/input/input9
[  132.214454] input,hidraw0: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:1d.7-8.3
[  132.232122] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8.3/5-8.3:1.1/input/input10
[  132.258369] input,hidraw1: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:1d.7-8.3
[  132.260133] input: Logitech Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8.4/5-8.4:1.0/input/input11
[  132.310313] input,hidraw2: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:1d.7-8.4
[  132.310340] usbcore: registered new interface driver usbhid
[  132.310347] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  137.242756] [fglrx] interrupt source 10000000 successfully disabled!
[  137.242764] [fglrx] enable ID = 0x00000000
[  137.242769] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000008
[  140.809387] [fglrx] PCIe has already been initialized. Reinitializing ...
[  140.829363] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[  140.829368] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  140.829370] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[  140.829372] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[  140.954960] [fglrx] interrupt source 10000000 successfully enabled
[  140.954966] [fglrx] enable ID = 0x00000008
[  140.954976] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  158.496350] CPU0 attaching NULL sched-domain.
[  158.496355] CPU1 attaching NULL sched-domain.
[  158.520419] CPU0 attaching sched-domain:
[  158.520425]  domain 0: span 03
[  158.520426]   groups: 01 02
[  158.520431] CPU1 attaching sched-domain:
[  158.520432]  domain 0: span 03
[  158.520433]   groups: 02 01

**xorg.conf (fglrx 8.47.3 [Mar 29 2008] on minor 0 driver)** is down to basics now:
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableMonitor" "lvds,tmds1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

All kinds of help is deeply appreciated...

---

### Post by Strelock on 2008-05-23
Oh yes, one more thing after hot unplug from dock (after rmmod dock and /etc/init.d/atieventsd stop) ksoftirqd/0 uses 100% CPU time. as soon as the laptop is plugged back - its fine

---

### Post by Strelock on 2008-05-23
One more update:
using vesa driver do not resolve hotplugging issue

---

### Post by Strelock on 2008-05-24
bump?
suggestions anyone or should I file it as bug?

---

