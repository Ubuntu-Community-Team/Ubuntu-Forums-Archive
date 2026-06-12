---
title: "Brother MFC-8840D Not Printing/Waiting for printer to become available"
date: 2016-01-27
forum: Hardware
---

### Post by Chris_Cooley on 2016-01-27
Hello,

I'm running a headless Ubuntu 14.04.3 Server LTS, 64-bit with CUPS already installed.  A Brother MFC-8840D printer is connected via USB.  I've downloaded and installed the LPR and CUPS drivers from Brother.  After I installed the CUPS drivers, CUPS could then see the printer.  However, it will not print to it, just says "Waiting on printer to become available".  The connection is set to usb:/dev/usb/lp0, but that's the tricky part.  When I plug the printer in, a device file is created in /dev/usb.  After I search for the printer in CUPS (which fails), the device file is removed.  I'm pretty sure this is by design since hplip and lpusb? is moving it to /dev/bus/usb/...

I've looked at log messages (dmesg) and noticed apparmor was causing an issue which I've since resolved.  I think I entered something like "sudo aa-complain cupsd" to get apparmor to stop giving me DENIED messages.  hplip is not installed.  

At this point I'm very confused on the whole Linux printer installation between the driver and CUPS.  This is a file server running Samba, and the printer is not networkable.  I'm going to make the printer networkable via CUPS/Samba like it was once before.  I don't know if it's the latest version of Ubuntu, but I've had this thing working before, even the scan to file feature.  I've tried so many different things and read so many different solutions.  Any help will be greatly appreciated!

Thank you

---

### Post by Chris_Cooley on 2016-01-28
Anybody?

---

### Post by Chris_Cooley on 2016-01-28
I solved this, finally.  For anybody in the future with a similar issue, this is what I did:

1. Entered lsusb to get the device ID of the printer which was 04f9:0160
2. Created a new file:  touch /etc/udev/rules.d/10-cups-usb.rules
3. Added this line to the new file:  ATTR{idVendor}=="04f9", ATTR{idProduct}=="0160", MODE:="0664", GROUP:="lp", ENV{libsane_matched}:="yes"

Rebooted the server and CUPS now detects the printer as a local printer.  You can probably just restart CUPS rather than rebooting.

---

