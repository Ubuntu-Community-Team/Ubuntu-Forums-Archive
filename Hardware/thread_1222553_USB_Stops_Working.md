---
title: "USB Stops Working"
date: 2009-07-25
forum: Hardware
---

### Post by Enjeru on 2009-07-25
Hey guys,

The home computer that my parents use works flawlessly other than the fact that if it has been on for more than half a day, all USB devices stop functioning, and the only way to fix it is either to restart the computer or restart the x-server.  Though the latter isn't hard to do, I am wondering if there is a more permanent solution to this problem.  Here are the PC hardware and software specs: [Click](http://www.newegg.com/Product/Product.aspx?Item=N82E16883118008).

---

### Post by wojox on 2009-07-25
You can look in /etc/defaults/acpi-support

cd /etc/default
sudo cp -p acpi-support acpi-support.bak
sudo gedit acpi-support
Change MODULES="" to MODULES="ehci_hcd"

---

