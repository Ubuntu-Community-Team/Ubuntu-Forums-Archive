---
title: "Accessing ubuntu printer from XP"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by sputnik on 2005-01-18
Found this
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#networkprinter](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#networkprinter)
& this
[http://www.ubuntulinux.org/wiki/NetworkPrintingFromWin2K](http://www.ubuntulinux.org/wiki/NetworkPrintingFromWin2K)

> # A line that has Listen 127.0.0.1:631 can be replaced by Port 631 to listen on all network interfaces, or, if you have a more complex setup and don't want to listen on all interfaces,you can add additional Listen lines for each IP address that you want it to hear.

Do I need to change firestarter configuration to allow port 631?

> restarted cups with the command

    *      /etc/init.d/cupsys restart
When I tried this I got :
 /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System...
cupsd: Child exited with status 99!                                      [ ok ]
 Any ideas what this means, or where I find the answer?

---

