---
title: "How to tell if I'm using USB2?"
date: 2008-07-25
forum: General Help
---

### Post by yang on 2008-07-25
How do I tell whether my external disks are plugged into USB2 ports?

Also, a separate but related question: is there an easy way (without opening my case) to tell which ports are USB2 ports?

I'm currently getting 8.6 MB/s but that's transferring from external to external.

Thanks in advance for any help!

---

### Post by ModelM on 2008-07-25
Plug one in, wait a few seconds and type into a terminal:

tail -25 /var/log/messages

You should see a line saying "new usb device..." or some such. Look for "EHCI", that's the USB 2.0 driver. OHCI & UHCI are USB 1.1 drivers.

---

