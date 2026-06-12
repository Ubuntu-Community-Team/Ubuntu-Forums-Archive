---
title: "syncing Palm -- USB service hangs"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by redwing57 on 2006-11-15
Synopsis:
I am experiencing unreliable syncing with my Palm Tungsten E.  A complication is that the handshake between the Palm and the USB system hangs in a state that I am only able to escape by rebooting.

Detail description:
I am running Ubuntu 6.06.1 (Dapper) and using a Palm Tungsten E.  I have been syncing with Jpilot (so far the only application I can successfully sync with).  The procedure is to press the hotsync button on the palm, count to 2, and then click the hotsync button in Jpilot.  When it works, no worries.  When it doesn't, the device is not properly disconnected.  All subsequent attempts to sync will (often, if not always) fail (the driver does not seem to start, ttyUSB0 and ttyUSB1 are not assigned, and /dev/pilot is not created).

/var/log/kern.log for a good sync:
Nov 15 16:09:05 eagle kernel: [17181682.448000] usb 4-2.1: new full speed USB device using ehci_hcd and address 6
Nov 15 16:09:05 eagle kernel: [17181682.556000] visor 4-2.1:1.0: Handspring Visor / Palm OS converter detected
Nov 15 16:09:05 eagle kernel: [17181682.556000] usb 4-2.1: Handspring Visor / Palm OS converter now attached to ttyUSB0
Nov 15 16:09:05 eagle kernel: [17181682.556000] usb 4-2.1: Handspring Visor / Palm OS converter now attached to ttyUSB1
Nov 15 16:09:17 eagle kernel: [17181694.768000] usb 4-2.1: USB disconnect, address 6
Nov 15 16:09:17 eagle kernel: [17181694.768000] visor ttyUSB0: Handspring Visor / Palm
OS converter now disconnected from ttyUSB0
Nov 15 16:09:17 eagle kernel: [17181694.768000] visor ttyUSB1: Handspring Visor / Palm
OS converter now disconnected from ttyUSB1
Nov 15 16:09:17 eagle kernel: [17181694.768000] visor 4-2.1:1.0: device disconnected

/var/log/kern.log for a failed sync:
Nov 15 16:12:19 eagle kernel: [17181876.196000] usb 4-2.1: new full speed USB device using ehci_hcd and address 8
Nov 15 16:12:22 eagle kernel: [17181879.284000] usb 4-2.1: device descriptor read/64, error -110
Nov 15 16:12:37 eagle kernel: [17181894.476000] usb 4-2.1: device descriptor read/64, error -110

As the palm keeps trying to connect, the errors repeat, but the address increments, so the next error would look like the above, but the address would be 9.

Hopefully this information will help somebody to solve the problem, but in the mean time, it would be nice to be able to reset the process or module that is hung up, without rebooting.

Rob

---

### Post by jonrkc on 2007-01-20
Same thing happening here with Dapper 6.06 and a Tungsten E.  I read about the incrementation on a Fedora forum (Google'd).  JPilot will never recognize the device unless the ttyUSB number in its settings is the same as the newly assigned number.  But even when I laboriously do this, no connection is possible.  JPilot will say it's attached, etc., but no possibility of sync'ing since the connection FROM the Palm is how the Palm gets a USB number in the first place--and you can only break the connection (cancel button), not make it, as JPilot expects ("Please press the SYNC button now.")  The button no longer exists.

This is due to some upgrade between December 28 and probably the first week of January.  It was working perfectly every time (better than ever, in fact) up through December 28.  

I wish I hadn't upgraded whatever got upgraded after that.

---

### Post by redwing57 on 2007-01-23
I switched my office and one of my home computers to CentOS 4.4 because syncing is much more reliable.  Rebooting Ubuntu to reset the USB system was unacceptable.  CentOS syncs successfully about 90% of the time -- still not good.  I sure hope this gets fixed, because the Palm Pilot is nearly as important to me as the computer.

---

