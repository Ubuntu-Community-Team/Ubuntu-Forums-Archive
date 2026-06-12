---
title: "Where to put PPD so CUPS web utility sees it"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by ktritty on 2009-06-06
Surprised that my search cannot find answer to this one:

What directory should I stick a PPD file in so that when I use the CUPS web utility to add a printer, I will see it in the drop menu?

The web utility has a Browse feature, but I cannot get it to work right.  I run CUPS web utlity from my MacBook, and when I try to browse, it browses my MacBook and not my Ubuntu server.  When I try to run CUPS web utility via lynx on the Server, it still does not work.  This is frustrsating, because I have the PPD prescribed by openprinting.org, but I can't get CUPS to find it!

So, if someone can help me figuer out where to 'mv the ppd', I will be very grateful!

---

### Post by munky99999 on 2009-06-06
/etc/cups/ppd

I think. At least that is where it is. Good luck.

---

### Post by ktritty on 2009-06-06
Thanks, that is the right place.

But I can't get my printer to run.  I spent 7 hours getting my other one to run, getting my feet wet with apt-get and cups and ufw and so forth.  O thought adding a second one would be a snap for sure.

The same tricks aren't working for this one.  (Very frustrating because I plugged it into my MacBook and right away was able to press command-p and succeed at printing). But I want it hooked up to my ubuntu server for obvious reasons.

Printer model:HP PSC 1410v (uses 1400 Series ppd, recommended by openprinting, works when plugged into MacBook USB socket)

What I've tried that seemed the closest to working:
1) CUPS Web interface [http://server:631/admin](http://server:631/admin)
2) press "find new printers" link, It detects it and names it properly.
3) click "add this printer", the default name, location, and description are correct, based on my experience adding other printers on other ubuntu computers.
4) the system comes up with the driver selection window.  I manually point it to the right file I got from openprinting, in /etc/cups/ppd/
5) Cups thinks it succeeded.
6) when I try to print test page, it halts, and there is a message next to the printer nme in cups: [FONT=Arial][SIZE=2]"/usr/lib/cups/filter/foomatic-rip failed"[/SIZE][/FONT]

Note: cups assigns it the following **Device URI:** usb://HP/PSC%201400%20series?serial=CN562B40T504BN

Should I try to add the printer manually using some other setting?

Added Note: "Filter "foomatic-rip" for printer "HP_PSC_1400_series_USB" not available: No such file or directory" is the error message that comes up on my MacBook when I try to add it via Cups Web utility to my MacBook (it also fails this way), altough it succeeds plug&play in the MacBook.  Although, when I try to look up the URI that my MacBook gave it in Plug & PLay mode, it says "URI is file://dev/null/" which I find odd, but it works.

Thanks!

---

