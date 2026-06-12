---
title: "Printing Firefox Postscript"
date: 2004-11-22
forum: Hardware &amp; Laptops
---

### Post by ljoris on 2004-11-22
[QUOTE=steveb]I set up two printers on Ubuntu. A hp2000 and an networked hp laserjet 5.  Both work with openoffice.  From Firefox the printers do not appear in the file->print menu. Only a postscript printer appears. I've saved the postscipt output and opened it with Ghostview but can not print form Ghostview. Again neither printer appears in the print menu.

How do I print from Firefox to these printers.

Thanks 
Steve[/QUOTE]

I trust you used your gui to set these up ? And you've set them up with the same user you're trying to print with ?

---

### Post by steveb on 2004-11-22
I set up two printers on Ubuntu. A hp2000 and an networked hp laserjet 5.  Both work with openoffice.  From Firefox the printers do not appear in the file->print menu. Only a postscript printer appears. I've saved the postscipt output and opened it with Ghostview but can not print form Ghostview. Again neither printer appears in the print menu.

How do I print from Firefox to these printers.

Thanks 
Steve

---

### Post by dspivey on 2004-11-23
Assuming you installed your printers by using System Configuration > Printing, Firefox will print to your default printer, even though you can't select a printer from the Firefox print dialog.  Every application is responsible for how it prints in Linux; as you've already seen, printing in Linux is not universal across all applications, even on a great distro like Ubuntu.  This is something sorely lacking in Linux when compared to Mac OS X (which uses CUPS as well).

---

### Post by wazoo on 2004-12-24
Well this is interesting. I installed an HP Laserjet 1200, which works fine -- except for the applications that don't know it's there. Firefox doesn't list it, but if I just accept Postscript/Default, it works anyhow.

Other applications -- installed with sudo permissions via dpkg, don't find the printer, presumably because I set it up as a user?

---

### Post by steveb on 2004-12-27
Most of my problems turned out to be in the setting up of CUPS. For Firefox if you go to print > properties for the postscript printer you'll find that the command used is "lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}" or the cups print command.

---

