---
title: "ATI X.org setup?"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by Gibbz on 2005-01-22
okay dont remember how i installed the driver last time. Ive downloaded and installed the driver through synamptic. Now im upto the part of editing 'xorg.conf'

all i have changed in there is this section so it looks like bellow....
Anyone know why its not working(3d acceleration). Did i miss a step?

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option		"UseInternalAGPGART" "no"
EndSection

---

### Post by jensyt on 2005-01-22
Do you mind attaching your entire xorg config and the contents of /var/log/Xorg.0.log?

Also, what happens when you run fglrxinfo?

---

### Post by shmonkey on 2005-01-23
Yes you need to run /usr/X11R6/bin/fglrxconfig also make sure you have the restricted modules installed for your kernel. e.g. ```
sudo apt-get install linux-restricted-modules-k7
``` for AMD

---

