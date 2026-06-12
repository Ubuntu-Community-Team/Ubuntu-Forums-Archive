---
title: "LPR printer"
date: 2015-11-26
forum: Hardware
---

### Post by lazyest on 2015-11-26
Got similar issue like [http://ubuntuforums.org/showthread.php?t=1925728](http://ubuntuforums.org/showthread.php?t=1925728)
Have STLabs N340 print server and Samsung ML-1210 printer. Tested with ubuntu from 12.04 up to 15.10 now, nothing changes, spooling 0% and thats all. What can I debug to figure out what can be fixed? MacOS 10.6.8 working out of box and windows XP/7 too.

---

### Post by efflandt on 2015-11-27
Unfortunately there are not many details on that printer or print server. The only Emulation that printer lists is "PrinThru, but the fact that Linux instructions for it (for RedHat) mention installing ghostscript means that it likely understands postscript. I don't know if Ubuntu has a driver for that specific printer and it has been many years back in the lpd/lpr /etc/printcap days that I simply configured a Xerox printer with no driver to simply use "generic level 2 postscript" (which worked). But maybe it would work for any other printer that emulates postscript as one of its printer languages (I don't know if it necessarily needs to be 600 dpi like your printer).

It looks like the print server only does lpd/lpr printing. That should not be a problem for cups. For the network printer location you would use a URL of lpd://hostname/queue (where hostname could be its IP address and you could try **auto** or **raw** for the queue). If there is no such queue, it would likely use its default queue.

If you want to do cups administration from a web browser ( [http://localhost:631/](http://localhost:631/) ), which gives more details than System Settings > Printers, I believe you need to be a member of group **lpadmin**. Assuming that you are a user that can use sudo, you could add yourself to that group with:```
sudo gpasswd -a your_username lpadmin
```

---

### Post by lazyest on 2015-11-29
I have Samsung ML-1210 printer, working fine with ubuntu via USB cable. I have a cheap print-server, [http://www.priceme.co.nz/STLab-N-340/p-883187829.aspx](http://www.priceme.co.nz/STLab-N-340/p-883187829.aspx). When Trying to use this pair with Ubuntu have 0% spooling forever, from windows and macos having no problem. All CUPS access and so on is OK.
I've tried to use all detected queues (PASSTHRU, PS, PORT1 and DEFAULT) without any changes.

---

