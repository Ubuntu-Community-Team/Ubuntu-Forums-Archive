---
title: "printing?"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by thechris on 2006-01-01
cannot print.  epson stylus color 900.  gimp-print driver.  parallel port.  gets detected, will not print anything.  if i turn the printer off, then back on, it will print 1/2 of a test page incorrectly.  works in windows.  it seems i cannot downgrade to 5.04's cupsys, which did work.

---

### Post by No-Brain on 2006-01-01
The following is quoted from a reply I made to someone else with printing problems. CUPS has an error-log that you can turn on. This might help you to find your problem.

The following is what i did to set the error-log:

cd /etc/cups/
sudo gedit cupsd.conf (or whatever you use for a standard thext editor)

Look for an entry called "LogLevel" no quotes

change the word after "LogLevel" to debug and save the file.

It probably would not hurt to restart your PC.

Try to print something.

CD to /var/log/cups

There is a file called error-log

You need to display this file i.e. I use gedit to browse the file.

Look for an error.


Good Luck
Roger

P.S. I found it helped to clear the log file, and reboot to reinialize the log file. That way, you are only reading the log file for the current session.

---

