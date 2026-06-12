---
title: "HP P1007 laserjet errors post installation"
date: 2008-09-16
forum: Hardware
---

### Post by kennedyjch on 2008-09-16
I've recently installed a HP p1007 laser printer on my Ubuntu 8.04 system using the procedure outlined in [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html).

Printer is recognized and occassionally prints. However it frequently encounters an error (code 1806 "service request" in HP device manager).

Anyone have any insights as to what the solution is?

I've also done "tail -f /var/log/messages" with the results given below. Of concern is the message that "hp-makeuri should not be run as root" - but this is how the installation process set it up...

Any help/pointing in the right direction would be appreciated...


Sep 16 17:49:43 john-desktop-l kernel: [40717.777890] usb 1-6: new high speed USB device using ehci_hcd and address 8
Sep 16 17:49:43 john-desktop-l kernel: [40718.193513] usb 2-6: new full speed USB device using ohci_hcd and address 8
Sep 16 17:49:43 john-desktop-l kernel: [40718.396752] usb 2-6: not running at top speed; connect to a high speed hub
Sep 16 17:49:43 john-desktop-l kernel: [40718.420836] usb 2-6: configuration #1 chosen from 1 choice
Sep 16 17:49:43 john-desktop-l logger: loading hp_laserjet_p1007 firmware 002 008
Sep 16 17:49:43 john-desktop-l kernel: [40718.430789] usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4817
Sep 16 17:49:44 john-desktop-l python: hp-firmware[21201]: warning: hp-firmware should not be run as root.
Sep 16 17:49:45 john-desktop-l python: hp-makeuri[21217]: warning: hp-makeuri should not be run as root.
Sep 16 17:49:45 john-desktop-l python: hp-makeuri[21221]: warning: hp-makeuri should not be run as root.
Sep 16 17:49:47 john-desktop-l kernel: [40721.828956] usblp0: removed
Sep 16 17:54:52 john-desktop-l kernel: [41026.486197] audit(1221567892.128:5): type=1502 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=21370 profile="/usr/sbin/cupsd" namespace="default"
Sep 16 17:58:50 john-desktop-l kernel: [41264.309215] audit(1221568130.164:6): type=1502 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=21472 profile="/usr/sbin/cupsd" namespace="default"
Sep 16 18:00:01 john-desktop-l kernel: [41336.041536] audit(1221568201.960:7): type=1502 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=21555 profile="/usr/sbin/cupsd" namespace="default"
Sep 16 18:07:40 john-desktop-l kernel: [41793.868831] audit(1221568660.199:8): type=1502 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=21725 profile="/usr/sbin/cupsd" namespace="default"
Sep 16 18:08:44 john-desktop-l python: hp-toolbox(UI)[21763]: warning: Device not found
Sep 16 18:15:06 john-desktop-l python: hp-toolbox(UI)[21763]: warning: Device not found
Sep 16 18:16:06 john-desktop-l last message repeated 2 times

---

### Post by kennedyjch on 2009-01-08
Update: 2.8.10 driver from HP works on 8.04 and printer operates flawlessly. However, under Ubuntu 8.10, niether 2.8.10 nor 2.8.12 driver installations from HQ function. Further, attempting to print kills my UBS wifi connection. So appears to be a problem with the ubs driver. 

Any clues?

---

### Post by kennedyjch on 2009-01-12
Solution! It appears that I had to move the printer to another USB port. Now printer works!

---

### Post by kennedyjch on 2009-11-11
Update Ubuntu 9.10 - After upgrading from 9.04 to 9.10 printer did not work. Was able to reinstall cups and hplip and after some fiddling it would work intermittently. Problem was that there was intermittent communication with the USB printer.

However, with the recent update of cups, printer works just fine.

---

