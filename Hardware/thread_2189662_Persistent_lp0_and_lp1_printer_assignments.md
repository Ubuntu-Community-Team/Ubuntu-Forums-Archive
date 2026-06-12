---
title: "Persistent lp0 and lp1 printer assignments"
date: 2013-11-23
forum: Hardware
---

### Post by JoeSabido on 2013-11-23
I made a software using PHP that needs to have two printers attached, one for receipts and one for labels.

Both printers are exactly the same (Epson TM-T81 USB) and the only difference being between them is the type of paper that is loaded. Printing is performed by writing directly to the printer ports /usb/lp0 or /usb/lp1 using fopen() which has worked pretty good so far!

The problem now is that I don't know how to make /usb/lp0 and /usb/lp1 always link to the same printer so that I can always print receipts to LP0 and labels to LP1, without having to worry about which printer I plug in/power on first.

How can I achieve this? 

Can someone help or point me to similar posts? I don't know what to search for.

Thanks

---

