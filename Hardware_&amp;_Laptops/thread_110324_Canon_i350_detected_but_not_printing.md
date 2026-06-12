---
title: "Canon i350 detected but not printing"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by GMathews on 2005-12-30
Canon i350 detected but not printing. Cant add to printers. Plz help.

---

### Post by No-Brain on 2005-12-31
I got my printer working by setting the cups log file to debug.  Do the following to enable the log file

cd /etc/cups/
sudo gedit cupsd.conf  (or whatever you use for a standard thext editor)

Look for an entry called "LogLevel"  no quotes

change the word after "LogLevel" to debug and save the file.

It probably would not hurt to restart your PC.

Try to print something.

CD to /var/log/cups

There is a file called error-log

You need to display this file i.e.  I use gedit to browse the file.

Look for an error.

In my case, it said I needed a file.

Once I installed the file, my printer worked.  Only took my a week or two to get it working. You may want to post the error-log here, if you cant find a problem.  I got lucky with mine, you may also.

Apparently it is a common problem.  No one ever responded to my request for help, and you can find several requests in the forums that went unanwsered as well.


Roger

---

### Post by coolclassic on 2005-12-31
Try the drivers from [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) They have an excellent trak record for supporting printers in linux

---

