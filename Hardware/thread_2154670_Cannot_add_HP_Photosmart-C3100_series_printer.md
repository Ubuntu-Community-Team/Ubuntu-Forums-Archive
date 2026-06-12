---
title: "Cannot add HP Photosmart-C3100 series printer"
date: 2013-06-15
forum: Hardware
---

### Post by LLigetfa on 2013-06-15
Printer is connected to the network with HP JetDirect external unit.  Ubuntu discovers it but fails to add.

The following is in syslog.  Is there another place I should also look?
> 
Jun 15 10:45:11 HP-EliteBook-8540w dbus[992]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
Jun 15 10:45:11 HP-EliteBook-8540w dbus[992]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'
Jun 15 10:45:11 HP-EliteBook-8540w hp[4908]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:45:15 HP-EliteBook-8540w bluetoothd[1016]: Discovery session 0x7f6e854c35e0 with :1.83 activated
Jun 15 10:45:26 HP-EliteBook-8540w python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:45:40 HP-EliteBook-8540w hp[4959]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:45:44 HP-EliteBook-8540w bluetoothd[1016]: Discovery session 0x7f6e854c1070 with :1.85 activated
Jun 15 10:45:54 HP-EliteBook-8540w python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:47:05 HP-EliteBook-8540w dbus[992]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
Jun 15 10:47:05 HP-EliteBook-8540w dbus[992]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'
Jun 15 10:47:27 HP-EliteBook-8540w hp[5123]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:47:30 HP-EliteBook-8540w bluetoothd[1016]: Discovery session 0x7f6e854c35e0 with :1.90 activated
Jun 15 10:47:41 HP-EliteBook-8540w python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:48:14 HP-EliteBook-8540w dbus[992]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
Jun 15 10:48:14 HP-EliteBook-8540w dbus[992]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'
Jun 15 10:49:08 HP-EliteBook-8540w dbus[992]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
Jun 15 10:49:08 HP-EliteBook-8540w dbus[992]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'
Jun 15 10:49:09 HP-EliteBook-8540w hp[5177]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:49:12 HP-EliteBook-8540w bluetoothd[1016]: Discovery session 0x7f6e854c1070 with :1.95 activated
Jun 15 10:49:27 HP-EliteBook-8540w python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 15 10:56:04 HP-EliteBook-8540w dbus[992]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
Jun 15 10:56:04 HP-EliteBook-8540w dbus[992]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'

---

### Post by LLigetfa on 2013-06-15
Would details of the print server help?

HP JetDirect:	 J6035G
Firmware Version:	 M.25.54

I think Windows 7 is using port 9100 printing.  USB set to unidirectional.

---

### Post by LLigetfa on 2013-06-17
I tried running sudo hp-setup but it ended in an error and the test print at the end would not print.  Thought it might have something with how I setup the USB on the JetDirect but every other option produced the same result.

Then I noticed that every run of hp-setup resulted in a printer being setup in System Settings > Printers.  I deleted them all and tried hp-setup yet again with the same error.  I went back to System Settings > Printers and made it the default and tried a test print from there and it worked.  Tested it also from Chrome and that worked too.

---

