---
title: "Lost access to Ubuntu shared printer from Windows"
date: 2008-12-01
forum: General Help
---

### Post by 5circles on 2008-12-01
I installed a printer on my Ubuntu box, and got it working locally and from Windows.  But today it doesn't work across the network, just locally.

The message I'm seeing on the Windows systems is "Access denied, unable to connect".  The Windows systems can see the Ubuntu box and all the shares - including the printer.  I've tried removing the printer from Windows and reinstalling, but the message is still the same.

I checked the Ubuntu printer settings.  The printer server shows that printers are shared, and the policies show Enabled, Accepting Jobs, and Shared.  Access rights show that anyone can print.

The printer is an HP Deskjet 970.  I ran hp-check -t, and everything looks OK (warnings about scanners, but that's not relevant).

Any ideas?

---

