---
title: "Ubuntu &amp; Thinkpad Dock"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by devnulljp on 2005-11-30
I have a Thinkpad T41 with a dock. Printer, external HD, some other stuff all attached ot the dock. It worked fine under SuSE 9.2 & 3 but with Ubuntu I get weird USB errors and nothing works. 
My periphrals all work fine if plugged in directly to the TP's 2 USB ports but I'd like to use the dock.
Anyone else had any luck with this? Where to start?

---

### Post by devnulljp on 2005-12-09
Answering my own question in case anyone else runs into this. Disabling ohcp_hcd and ehcp_hcd modules allows the usb to work.
```

sudo modprobe -r ehci_hcd
sudo modprobe -r ohci_hcd
```

then lsusb shows the dock's USB and allows the drives to be mounted.

I've also blacklisted those modules in /etc/hotplug/blacklist

---

### Post by emendelson on 2005-12-09
Strange - on a T42 with a Dock II, the USB ports work perfectly out of the box with Breezy. Plug in a USB drive (using the Dock USB ports) and the drive mounts. I wonder if this is a T41 problem - and which dock are you using?

---

### Post by devnulljp on 2005-12-14
It's a Thinkpad [minidock ](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-55212) and it worked fine before without any tweaking with SuSE 8.x and 9.x and Gentoo. I'm not sure why the ohcp_hcd and ehcp_hcd modules make a difference, but disabling them seems to work.

---

