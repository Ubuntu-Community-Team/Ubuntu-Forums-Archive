---
title: "HP Laserjet 4 Not Working (Parallel Port)"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by sopordave on 2006-08-08
I've got a HP Laserjet 4 hooked up to LPT1 (printer and cable work on a Windows computer), but I can't seem to send any print jobs to it.  I've tried setting it up through the CUPS web interface and through the Printer Aministration window in Gnome.  It is not autodetected, but I tell it to use LPT #1 and give it the appropriate driver, and then CUPS claims that the printer is idle and ready.  But, I can't print anything.  Whenever I try to print, it creates a job and the Printer-Job thingie that pops up in the system tray says the printer is printing.  The job stays in there for what seems to be an appropriate time, and then disappears, but nothing comes out of the printer.

I've already searched the forums to see if there was already a solution for this, but none of their solutions seem to work for me.

Every time I try to send a print job, this appears in my log:
```
[17179652.840000] ppdev0: registered pardevice
[17179652.844000] ppdev0: unregistered pardevice

```

---

