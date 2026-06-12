---
title: "Problems installing Epson printer"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by Roque on 2006-11-16
I am trying to install an Epson C67 in Kubuntu Dapper.  

I wrote:
```

sudo apt-get install cupsys

```

But KDE's ControlCenter->Peripheals->Printers
fails when trying to Initialize the printer manager:
```

Unable to retrieve the printer list. Error message received from manager:
Connection to CUPS server failed. Check that the CUPS server is
correctly installed and running. Error: localhost: read failed (15).

```

I opened a console and typed:
```

lpinfo -v
<<after a long time:>>
lpinfo: Unable to connect to server: Connection timed out

```

But my usb printer seems to be detected:
```

lsusb
Bus 001 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 002: ID 0586:330a ZyXEL Communications Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

Does anybody know how to fix this or what to do next?
Many thanks in advance.

---

### Post by Roque on 2006-11-21
Anyone?

---

### Post by xcesarfrancox on 2007-07-28
Hi dude, try this thread

[http://ubuntuforums.org/showthread.php?t=206927](http://ubuntuforums.org/showthread.php?t=206927)

hope it helps

---

### Post by Roque on 2007-08-23
Thanks! I'll try it out

---

