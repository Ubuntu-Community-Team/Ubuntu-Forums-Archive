---
title: "Resolution problems"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by paul905 on 2008-04-05
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=746253](http://ubuntuforums.org/showthread.php?t=746253) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Think this has graduated to here since there seems no simple fix :-(

I just added a new Acer flatpanel monitor to a new Gutsy install.
AMD 690G graphics chipset.

The ideal resolution for the monitor is 1440 x 900 (widescreen)

However it comes up in 1024 x 768 and the only options Screens & Graphics gives me is 3 lower ones.

The core of my xconfig looks like this:

Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:5:0"
EndSection

Section "Monitor"
Identifier "Acer AL1716W"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Acer AL1716W"
DefaultDepth 24
SubSection "Display"
Modes "1440x1440" "1440x900" "1280x1280" "1280x1024" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection


My (probably dumb) solution was to delete all the low resolution options. However when I restarted xserver it could not use any of them and went into low graphics mode.

Any other driver options perhaps?

---

### Post by paul905 on 2008-04-06
Oh well - downloaded and installed Hardy...

Works wonderfully and looks beautiful - way to go - yayyyy!

---

