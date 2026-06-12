---
title: "How to Enable DRI?"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by akinwale on 2005-04-19
Hello,
I've searched through the forums for this but I wasn't able to get any helpful results. How can I enable DRI for my integrated VIA video? Warty Warthog 4.10 release with XFree86 4.3 I believe.

Thanks.

---

### Post by Vache on 2005-04-19
Which chip is it?

Post your lspci output, please.

---

### Post by akinwale on 2005-04-19
Here's the output:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)

---

### Post by Vache on 2005-04-19
In the X config file, under "Device", do you have the "via" driver? The onboard video is not going to give you spectacular 3D, obviously.

Also, in the same config file, in the "DRI" section, do you have "Mode 0666" ?

---



```

Section "DRI"
	Mode	0666
EndSection

```

```

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	Option		"NoDDCValue"		"1"
EndSection

```

---

### Post by akinwale on 2005-04-19
Here's what I have:

```
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection
```

and the DRI Section is exactly as you pasted.

---

### Post by akinwale on 2005-04-20
Can anyone please help? What could possibly be the problem?

---

### Post by Vache on 2005-04-20
[QUOTE=akinwale]Can anyone please help? What could possibly be the problem?[/QUOTE]
 glxinfo is telling you DRI is disabled? You might want to check the X log files, too.

---

