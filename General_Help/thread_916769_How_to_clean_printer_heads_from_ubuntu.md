---
title: "How to clean printer heads from ubuntu"
date: 2008-09-11
forum: General Help
---

### Post by irishrm on 2008-09-11
The heads on my epson 830u printer needed cleaning. Had to boot into windows to do so. Any way to do this in ubuntu.
Thanks irishrm.

---

### Post by oilchangeguy on 2008-09-11
> **irishrm said:**
> The heads on my epson 830u printer needed cleaning. Had to boot into windows to do so. Any way to do this in ubuntu.
Thanks irishrm.

not unless you can run the install cd for the printer. which is very doubtful. and it can't be that big of a deal to run windows, so you can clean the print heads. you need to run windows anyway, at least once a month. so it can stay current with updates, etc.

---

### Post by WRDN on 2008-09-11
There are multiple utilities available. You could use the [Stylus Toolbox]("http://stylus-toolbox.sourceforge.net/"), mtink or escputil (both in synaptic).

For escputil, you must use the command prompt for usage.

To clean the heads:

```
escputil -r /dev/usblp0 -c
```

To check the ink levels:

```
escputil -r /dev/usblp0 -s
```

To check nozzle:

```
escputil -r /dev/usblp0 -n
```

This assumes the printer is in usb port 0. To find what port it is in, open the Terminal and type:

```
lshw
```

Find the printer in the hardware list, and take note of the heading. E.g. it may say "-usb:0".

---

### Post by irishrm on 2008-09-11
Thanks for the quick replies.  It's good to have windows to fall back on but it would be nice to learn as much as possible about ubuntu so will try and follow what WRDN suggests
Thanks again-irishrm

---

### Post by fragos on 2008-09-12
Head cleaning on many printers can be initiated manualy at the printer. Feature like headcleaning and ink levels seem to depend on the printer being matched with a driver that understands the interface as defined by that vendor. HP provides the HPLIP Toolbox which gives access to all printer configuration and control features. I'm not familiar with Epson but I would think you need to look for a preferences tool like HPLIP Toolbox for Epson.

---

