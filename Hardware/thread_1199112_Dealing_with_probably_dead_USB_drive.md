---
title: "Dealing with probably dead USB drive"
date: 2009-06-28
forum: Hardware
---

### Post by zenlunatic on 2009-06-28
I carry a kingston mini slim on my keys.  It's basically a really small, thin drive.  I don't use this device often, but I recently put a couple files on there to back up.

I placed the device in the drive, and it's not auto mounting to the desktop.  Another drive works fine on the same port.  In the console I noticed some error messages.

I'm almost certain I have physically damaged the drive, although I popped off the case, and didn't notice any signs of breakage.
Here are some errors I get when I plug the drive in:

[ 1996.964279] usb 6-2: device descriptor read/64, error -71
[ 1997.188259] usb 6-2: device descriptor read/64, error -71
[ 1997.524280] usb 6-2: device descriptor read/64, error -71
[ 1997.748305] usb 6-2: device descriptor read/64, error -71
[ 1998.376225] usb 6-2: device not accepting address 44, error -71
[ 1998.905196] usb 6-2: device not accepting address 45, error -71
[ 1998.905271] hub 6-0:1.0: unable to enumerate USB device on port 2

---

### Post by ajgreeny on 2009-06-28
See if it works on a windows machine.  If so, make sure you "remove safely" using the system tray icon, and also perhaps just copy the files back to windows for the time being.  You can then try again in ubuntu and if it's still not seen try reformatting it with gparted.  Maybe the filesystem got corrupted in some way, but don't forget, usb flash drives have a limited life, long though that may be.

---

