---
title: "OpenChome, Laptop &quot;screen corruption&quot;"
date: 2012-11-23
forum: Hardware
---

### Post by fdm on 2012-11-23
I have an older laptop with a strange display issue. If I have an external monitor connected via VGA when starting X, the laptop's screen displays correctly. Without an external monitor connected, colors are displayed incorrectly(ex. white is rendered with a bluish tent). The screen artifects are black and red, persistent between sessions, GLX related, and can be "smeared" across the screen when moving windows.

Identification from lspci:
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)

Output of #sudo get-edid|parse-edid 
> get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0xc698d "VIA P4N800 PRO
"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

I have a comparison of my Xorg logs here:
[http://diffchecker.com/99oQi2eX](http://diffchecker.com/99oQi2eX)
On the left is with an external moniter, and the right is without. The only thing that caught my eye was the difference in screen physical size. When setting it in xorg.conf via the DisplaySize parameter, the issue still persisted.

I was able to work around this problem using an xorg.conf I found on some random post on the internet, but for the life of me I have been unable to reproduce that configuration. VESA does work very well, but anything(Windows) is better than that.

------

Seems I was able to solve this by downgrading to 12.04. Mesa 8 supports XAA which does not have the above issue and still had DRI1 code which is so much faster than llvm software acceleration. Win, win.

---

