---
title: "How to install samsung Printer/Scanner supported by samsung unified print driver"
date: 2012-10-15
forum: Hardware
---

### Post by Flanmaster on 2012-10-15
This is only for later flavors of ubuntu.  It appears that there is no longer any need for the samsung unified print driver in the newer versions/variants of ubuntu.  It appears to automatically recognize the printers that are supported by the samsung unified print driver.  after installation simply open the printer dialogue and "add printer", scanning as necessary.

If you have a networked printer/scanner but it wont scan, then simply modify the /etc/sane.d/xerox_mfp.conf file, the section that covers your printer to comment out the relevant "usb" line and add a line right below that says "tcp x.x.x.x" where x.x.x.x is the actual ip address of your printer/scanner.

Here is a link to the original post with the info on the scanner:
[http://www.pclinuxos.com/forum/index.php?topic=101096.0](http://www.pclinuxos.com/forum/index.php?topic=101096.0)

---

### Post by cariboo on 2012-10-21
This doesn't follow the Toots & TIps guidelines, moved to the Hardware sub-forum.

---

