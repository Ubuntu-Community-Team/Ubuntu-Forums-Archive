---
title: "Character set confusion"
date: 2008-12-01
forum: General Help
---

### Post by echofire on 2008-12-01
Can anyone who understands character sets shed some light on this please ?
- I use various Python programs to collect user data from Windows boxes across the world.  The data is transferred (mostly by FTP) to a Gutsy box, stored in a MySQL database, and extracted by other Python report generating programs.  The output of the programs, if sent direct to a terminal (console or PuTTY) is fine.  It is also fine if saved to a file and viewed with gedit, or transferred by FTP to a Windows box, from where it can be viewed and printed correctly
- The output, if stored to a file and viewed with less, contains <FC>, <E4> etc where the European characters should be.  It also will not print using CUPS to an HP Colour Laserjet 3600, where the printer aborts at the first u-umlaut, though this same printer prints the FTP'd version correctly
- Setting DefaultCharset in /etc/cups/cupsd.conf and restarting (sudo /etc/init.d/cupsys restart), or using export LANG=en_GB.iso-8859-15 makes no difference
- Along the same lines, does anyone know how to override the default character set to print from the command line using lp ?  The documentation covers the defaults but I can find no reference to overriding them.

Thanks
Nick

---

