---
title: "Epson Stylus USB printer troubles"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by Baka Dasai on 2006-03-02
I have a new Epson Stylus C87 USB printer. I'm running CUPS in Kubuntu Breezy.

I installed the printer using the Add Printer wizard in KDE. I used the Gutenprint v5.0.0.-rc2 driver for the Epson Stylus C88. It worked. I was *happy*.

But ever since that first happy day it hasn't worked. CUPS is running. The driver is installed. When I plug in the printer, dmesg indicates that my PC sees it:

```
[ 1611.717637] usb 2-1: new full speed USB device using ohci_hcd and address 3 
[ 1611.773160] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
```

But my jobs never print. They show up as "Queued" in KJobViewer. The printer shows as "stopped" in the KDE Control Panel.

When I try and print a test page from the KDE Control Panel, /var/log/cups/error_log shows:

```
Unable to open USB device "usb://EPSON/Stylus%20C87": No such device

``` 
I've tried removing the printer, and re-adding it, but I always get the same result.

What's gone wrong? Why did it work for a single day and then never again?

---

### Post by Baka Dasai on 2006-04-21
Nobody has any clue?

---

### Post by z_diver on 2006-04-21
[QUOTE=Baka Dasai]
```
Unable to open USB device "usb://EPSON/Stylus%20C87": No such device

``` 
I've tried removing the printer, and re-adding it, but I always get the same result.[/QUOTE]
I have a stylus cx4800 on Ubuntu breezy and my printer works great with the Gutenprint drivers - though it didn't work as well with the gimp-print drivers that came earlier.  

With the gimp-print 4.2 drivers, sometimes the connection to the printer seemed to change.  I had to add printer and fiddle around with creating printers with different connections.  But then it would work fine for a few weeks before poof... it would stop and I'd have to do it again.

But like I said, with the Gutenprint drivers I haven't seen this at all.  I know it's not a direct answer but maybe it will give you some ideas.

---

### Post by coolclassic on 2006-04-21
You say the printer is stopped you will be able to start again through the pull down menu.

---

### Post by Baka Dasai on 2006-04-21
[QUOTE=coolclassic]You say the printer is stopped you will be able to start again through the pull down menu.[/QUOTE]

If I start it through the menu it then shows as "Processing (accepting jobs)" for about 10 seconds before reverting to "Stopped (accepting jobs)".

---

### Post by coolclassic on 2006-04-21
"*Unable to open USB device "usb://EPSON/Stylus%20C87": No such device*"

You may be selecting wrong device try changing it in your print setup.

---

