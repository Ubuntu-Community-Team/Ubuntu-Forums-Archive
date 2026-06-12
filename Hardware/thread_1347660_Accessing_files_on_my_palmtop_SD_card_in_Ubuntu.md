---
title: "Accessing files on my palmtop SD card in Ubuntu"
date: 2009-12-06
forum: Hardware
---

### Post by Wtwine on 2009-12-06
Hi

I use a palmtop to enter data in spreadsheets, saved onto a SD card in the device.  The palmtop runs on Windows mobile.

Is there a way I can access files on the SD card in Ubuntu via USB  ie connect to the palmtop SD card as if it was a USB drive?  This would be simpler and faster than trying to synchronize eg using synce.

thanks

Wayne

---

### Post by Wtwine on 2009-12-07
Nevermind.  I sorted it out and it' easy.  At first, I wasn't able to explore files on my PDA via Synce because I got an error message saying something like "Nautilus can not open "synce" folders".  It turns out you also need to install the synce-gvfs plugin to enable Nautilus to function using Synce.  You can install sunce-gvfs in Synaptic.  It replaces the old synce-gnomevfs.

After installing the pugin and rebooting (important), I am now able to explore, copy and paste files between my PC running Ubuntu 9.04, and my PDA running on Windows Mobile and it's SD card, via Synce Tray>Explore ...

I can now design a spreadsheet in Open Office, save it in xls format, copy it and paste it into my PDA SD card via Synce and Nautilus, and open it on my PDA in Excel Mobile, and vice versa.

Piece of cake!

I hope this is helpful to somebody

Wayne

---

