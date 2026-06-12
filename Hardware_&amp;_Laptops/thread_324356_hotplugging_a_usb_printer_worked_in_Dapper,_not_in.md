---
title: "hotplugging a usb printer: worked in Dapper, not in Edgy"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by kkram13 on 2006-12-23
Took a while, but I got my printer (USB-connected HP Deskjet 3940) working with CUPS. Now, problem is as follows.
Girlfriend has a windows laptop (no worries, I'm working on her ;) ) and we share the printer. No print server as they're expensive. Also don't want to use one computer as a print server as that means both computers always need to be on, which is a waste of electricity. So depending on who needs to print, the cable is taken out and moved.

Under Dapper this worked fine - I boot my computer, then yank the cable out of the laptop and stick it in my computer and print. And vice versa. Under Edgy no such luck. Unless I boot with the printer connected -even with the printer off- it's not seeing it. CUPS will not detect it. Testpages don't print. Et cetera. I looked at what happens when tail -f /var/log/messages is on and nothing is seen. When cups is scanning, all it get is "hp-toolbox[10754]: warning: Device not found"

Any suggestions as to how to do this? It seems that somehow the USB port is not being scanned, I guess. I saw some threads on working with udev commands but frankly - it scares me.

Let me know if any other information is needed (computer details, log files etc.). Taa muchly for the help! And: merry christmas to one and all!

Doctor Zero

---

