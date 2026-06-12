---
title: "HP Laserjet 1100 USB"
date: 2014-05-17
forum: Hardware
---

### Post by name5 on 2014-05-17
I have an HP Laserjet 1100 Parallel printer with a USB to Parallel cable.  There are instructions to get it to work with Linux, but I have failed.  It works fine in Windows 7 (dual-boot).  Under System Settings->Printers I have HP-LaserJet-1100.  
Settings:
Description: HP LaserJet 1100
Location: ComputerName
Device URI: parallel:/dev/usb/lp0
Make and Model:  HP LaserJet 1100, hpcups 3.14.3

When I print a test page, it lists the job as submitted.  The job shows up in the print queue with a status Processing - Not connected?

I previously had this printer connected to a Linux desktop with a parallel port which I used as a Samba print server.  I have retired the desktop and want to print directly from my latop, which only has USB.  Does anyone have any troubleshooting recommendations?  I recently upgraded? to Ubuntu 14.04 which has broken quite a few things that I am still putting back together.  However, the printer did not work in 13.04 either.

---

### Post by Sef on 2014-05-17
The [HPLIP]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html") webpage says your printer does not work with usb. I would look into at getting a usb ot parallel adaptor.

---

