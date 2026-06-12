---
title: "Epson XP-800 WIFI Scanner"
date: 2018-10-12
forum: Hardware
---

### Post by bkowalski on 2018-10-12
Hello,

I spent few hours last night to install my Epson XP-800 wifi scanner and eventually landed on this link:
[URL="http://download.ebz.epson.net/dsc/search/01/search/searchModule"]download.ebz.epson.net/dsc/search/01/search/searchModule
[/URL]
I followed the installation recommendation from Epson and I get this error message when launching iscan:
Gtk-Message: 09:55:00.002: Failed to load module "canberra-gtk-module"

I went through several posts explaing how to install this but nothing got me fixed.

I eventually connected my Epson directly to my laptop and SimpleScan found it but g2scan did not. I wonder if there is a way to install this wifi scanner with Ubuntu?
Thank you for your help!

BK

---

### Post by him610 on 2018-10-12
With *simple scan*, you can choose to save your scanned image as *pdf*. In dropdown list under Document, choose Save As (Shift+Ctrl+S)

If it scans using *simple scan*, the driver is installed. I do not use *gscan2pdf* so I can not address it; however, it seems to take a **_lot_** of supporting packages. If you want to scan over your network, that is a different (networking) issue.

Added: On page 30 of the XP-800 User's Guide, there are instructions to select or change wireless network settings using your product control panel. Have you completed that yet? On page 286, there is a section, "Cannot Scan Over a Network" that refers to both Windows and OS-X, but you can basically use the same advice for Ubuntu.

---

