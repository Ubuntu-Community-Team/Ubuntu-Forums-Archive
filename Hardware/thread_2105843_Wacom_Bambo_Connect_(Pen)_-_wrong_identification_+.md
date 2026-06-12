---
title: "Wacom Bambo Connect (Pen) - wrong identification + wrong mapping in multi-monitor env"
date: 2013-01-17
forum: Hardware
---

### Post by aneganov on 2013-01-17
Hi all,

Recently I've purchased Wacom Bambo Connect (Pen) CTL-470 K. I plugged it into my computer and at first glance it worked. But after some investigations I figured out two problems:

Problem 1. The tablet is not identified by the system correctly. 
Problem 2. I can't map the tablet to one of my monitors.


[SIZE="3"]Incorrect identification[/SIZE]

**User interface**

On the settings form there is "Eraser pressure feel" control while CTL-470K lacks eraser feature:

[ATTACH]230175[/ATTACH]

**Kernel identification**

While connecting the table to PC syslog says:

```
Jan 17 12:39:23 eisenstein kernel: [ 1092.054875] usb 7-1: new full-speed USB device number 4 using xhci_hcd
Jan 17 12:39:23 eisenstein mtp-probe: checking bus 7, device 4: "/sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/usb7/7-1"
Jan 17 12:39:23 eisenstein mtp-probe: bus: 7, device: 4 was not an MTP device
Jan 17 12:39:23 eisenstein kernel: [ 1092.079637] input: Wacom Bamboo Connect Pen as /devices/pci0000:00/0000:00:1c.2/0000:07:00.0/usb7/7-1/7-1:1.0/input/input21
Jan 17 12:39:23 eisenstein kernel: [ 1092.081008] input: Wacom Bamboo Connect Finger as /devices/pci0000:00/0000:00:1c.2/0000:07:00.0/usb7/7-1/7-1:1.1/input/input22
```

As you see wacom kernel module creates two input devices: **Wacom Bamboo Connect Pen** and **Wacom Bamboo Connect Finger** - and while the former looks acceptable, the latter is pretending that device can "touch" while it really can't.

**lsusb identification**

```
...
Bus 007 Device 005: ID 056a:00dd Wacom Co., Ltd
```

VendorId: 0x056a (well, this is Wacom)
DeviceId: 0x00dd (Unknown)

i.e. not much info.

**xsetwacom identification**

```
$xsetwacom --list devices 
```

outputs this:

```
Wacom Bamboo Connect Finger touch	id: 8	type: TOUCH     
Wacom Bamboo Connect Finger pad 	id: 9	type: PAD       
Wacom Bamboo Connect Pen stylus 	id: 14	type: STYLUS    
Wacom Bamboo Connect Pen eraser 	id: 15	type: ERASER
```

Wow! Like I have even 4 devices, while only **Wacom Bamboo Connect Pen stylus (id: 14)** looks appropriate.

Any ideas how to bring discipline to this mess?

[SIZE="3"]Problem with mapping to monitors[/SIZE]

I have 3 physical displays but I can map the tablet only to the first (DVI-D-0) and third (VGA-0), but not the second (DVI-D-1). When in the settings form I select DVI-D-0 or VGA-0 corresponding item in dconf 

```
org/gnome/settings-daemon/peripherals/wacom/usb:0x56a:0xdd -> display
```

is changed either to ['VSC', '14376', '16843009'] or ['ACR', '44416', '0'], but when I select DVI-D-1, this item's value stay unchanged, and after closing and opening "Map to single monitor" dialog UI change isn't saved too. See the screenshot:

[ATTACH]230176[/ATTACH]

---

### Post by Favux on 2013-01-17
Hi aneganov,

Problem 1.  Not a problem, expected results.  The other third generation BambooPTs have touch and a pad and might have an eraser.  The Wacom X driver handles the firmware the same and appends the daughter devices stylus and eraser to Pen and touch and pad to Finger.  Even though with the DD you just have the Pen.  See:
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)

Problem 2.
This looks to be a real bug with MapToOutput I have seen before.  Maybe MapToOutput isn't parsing past DVI?  So it can't distinguish between -D-0 or -D-1?

You could try a CTM and see if that works:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

Otherwise I would suggest posting to linuxwacom-discuss and see if a dev will help you.
[https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

---

