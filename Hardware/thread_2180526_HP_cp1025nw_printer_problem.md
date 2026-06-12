---
title: "HP cp1025nw printer problem"
date: 2013-10-13
forum: Hardware
---

### Post by phoenix1963 on 2013-10-13
Having worked perfectly until now (and on the previous system before I upgraded), somehow CUPS can no longer print to the printer. I can view the printer as a web server, can uninstall/install it under the CUPS webserver...
Here's a copy of what might be the offending log messages:
```

D [13/Oct/2013:16:30:33 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Oct/2013:16:30:33 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Oct/2013:16:30:33 +0100] [Job 41] STATE: +hplip.plugin-error
D [13/Oct/2013:16:30:33 +0100] PID 2500 (/usr/lib/cups/filter/hpcups) stopped with status 1.
D [13/Oct/2013:16:30:33 +0100] PID 2499 (/usr/lib/cups/filter/gstoraster) stopped with status 13.
D [13/Oct/2013:16:30:34 +0100] [Job 41] prnt/hpcups/HPCupsFilter.cpp 435: m_Job initialization failed with error = 48DEBUG2: hrDeviceDesc="HP LaserJet CP1025nw"
D [13/Oct/2013:16:30:34 +0100] [Job 41] prtGeneralCurrentLocalization type is 5, expected 2!
D [13/Oct/2013:16:30:34 +0100] [Job 41] backendWaitLoop(snmp_fd=5, addr=0x7f9f8829b9b8, side_cb=0x7f9f86307180)
D [13/Oct/2013:16:30:34 +0100] [Job 41] Connecting to nnn.nn.n.nnn:9100
I [13/Oct/2013:16:30:34 +0100] [Job 41] Connecting to printer.
D [13/Oct/2013:16:30:34 +0100] Discarding unused job-progress event...

```

In the belief that I'm missing a proprietary hplib plug-in, I've gone to [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_cp_1025nw.html]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_cp_1025nw.html"), which tells me that there's an installer already in my distro.
Maddeningly, if I try (having added qt):
```

sudo hp-plugin

```
it hangs because it can't contact [http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.12.2-plugin.run]("http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.12.2-plugin.run"), basically openprinting.org seems broken.
Also weirdly, this hp supported site doesn't list it as supported [http://hplipopensource.com/hplip-web/supported_devices/color_laserjet.html]("http://hplipopensource.com/hplip-web/supported_devices/color_laserjet.html"), despite the entry above, so I can't download the latest hplib from it to install (because it asks for a supported printer).

Has anyone got a copy of the plug-in maybe, or another suggestion?

phoenix1963

---

### Post by phoenix1963 on 2013-10-14
Well, I've managed to solve it, why the distro doesn't do it this way I don't know. I hope this is of use to others.

A solution can be found here [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/"), this extraordinarily helpful person has written a build for various printers that use the [http://web.archive.org/web/20020830075425/http://ddk.zeno.com/Reference/ZjStream/Default.htm]("http://web.archive.org/web/20020830075425/http://ddk.zeno.com/Reference/ZjStream/Default.htm") protocol. I just hope it is entirely legit, as I worry about compiling and installing something this complex without having many eyes check it.

It seems very effective and comprehensive. It's important to read the distro section in the instructions.

phoenix1963

---

### Post by phoenix1963 on 2013-10-14
Sorry, posted in error trying to mark it SOLVED...

---

### Post by phoenix1963 on 2013-10-14
I'm adding the list of printers supported by this fix so a search may find them:
HP LaserJet Pro CP1025nw
HP Color LaserJet CP1215
HP Color LaserJet 1500
HP Color LaserJet 1600
HP Color LaserJet 2600n

Konica Minolta magicolor 1600W
Konica Minolta magicolor 1680MF
Konica Minolta magicolor 1690MF
Konica Minolta magicolor 2480 MF
Konica Minolta magicolor 2490 MF
Konica Minolta magicolor 2530 DL
Konica Minolta magicolor 4690MF
Oki C110
Xerox Phaser 6115MFP
Xerox Phaser 6121MFP.ICM files

Minolta Color PageWorks/Pro L
Minolta/QMS magicolor 2200 DL
Minolta/QMS magicolor 2300 DL
Konica Minolta magicolor 2430 DL

Samsung CLP-300
Samsung CLP-315
Samsung CLP-325
Samsung CLP-365
Samsung CLP-600
Samsung CLP-610
Samsung CLX-2160
Samsung CLX-3160
Samsung CLX-3175
Samsung CLX-3185
Xerox Phaser 6110 and 6110MFP

Lexmark C500

Oki C301dn
Oki C310dn
Oki C3200
Oki C3300
Oki C3400
Oki C3530 MFP
Oki C5100
Oki C5200
Oki C5500
Oki C5600
Oki C5800

Olivetti d-Color P160W

HP LaserJet 1000
HP LaserJet 1005
HP LaserJet 1018
HP LaserJet 1020

HP LaserJet P1005
HP LaserJet P1006
HP LaserJet P1007
HP LaserJet P1008
HP LaserJet P1505

phoenix1963

---

