---
title: "Problems with Printing to BJC-4400"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by Julian_Kolm on 2005-12-30
I have no idea why it suddenly got impossible to print.

When I try to print a Testpage I recieve the following error message

"Printing to 'BJC-4400' failed with error code: 1033
is the printer paused ?"

The Printer Is able to Print another  Testpage if I order it to do so manually by pressing the resume button.

Thank you for helping

---

### Post by No-Brain on 2005-12-31
The following is quoted from a reply I made to someone else with printing problems.  CUPS has an error-log that you can turn on.  This might help you to find your problem.

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

P.S.  I found it helped to clear the log file, and reboot to reinialize the log file.  That way, you are only reading the log file for the current session.

---

