---
title: "HP Officejet 5510 - makes sounds but does not print"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by littlegreenman on 2007-03-21
Hi,

I have a HP Officejet 5510 printer installed on a windows xp machine. Through Samba I was able to get it connected. The problem is that when I print a test page, or anything for that matter, the printer starts making some sounds, it seems like it is going to print, the light starts flashing, but then nothing....

I am running kubuntu.

I have tried restarted cups with the command that i saw posted here in the forum, but didn't work.

Thank you for all your help.
Diogo

PS - The printer works fine when printing under xp.

==== UPDATE====

I did
```
sudo /etc/init.d/cupsys restart
```

and then
```
sudo /etc/init.d/cupsys restart
```

and got the log:
```
diogo@diogo-laptop:~$ tail -f /var/log/cups/error_log
I [21/Mar/2007:20:26:05 +0000] Configured for up to 100 clients.
I [21/Mar/2007:20:26:05 +0000] Allowing up to 100 client connections per host.
I [21/Mar/2007:20:26:05 +0000] Using policy "default" as the default!
I [21/Mar/2007:20:26:05 +0000] Full reload is required.
I [21/Mar/2007:20:26:05 +0000] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [21/Mar/2007:20:26:05 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [21/Mar/2007:20:26:05 +0000] Full reload complete.
E [21/Mar/2007:20:26:05 +0000] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
I [21/Mar/2007:20:26:05 +0000] Listening to /var/run/cups/cups.sock on fd 2...
E [21/Mar/2007:20:26:05 +0000] cupsdStartBrowsing: Unable to bind broadcast socket - Address already in use.
```

Could it be something here?

---

### Post by Sensei_V on 2007-11-20
I have the exact same problem with a different printer from my Ubuntu 7.10 laptop.  It's a Sharp MX-2300N at the office where I work.  The job shows up as completed in CUPS, and the printer wakes up when the job is sent, but no printout.

I would like to start installing Linux on some of the desktops at work, but the lack of printing is a deal-breaker.

---

### Post by Phitherek_ on 2008-06-13
I have the same problem even on Kubuntu 8.04 with a PPD installed from linuxprinting.org. I connect via WLAN (my computer is connected directly to wireless router). On the ubuntu.pl forum is nobody who knows a solution. Maybe here? (Sorry for my English).

---

### Post by Sensei_V on 2008-07-14
Normally I wouldn't post to a thread this old, but since Phitherek asked, I'm posting an update.

It turned out that the printer I was using didn't support PostScript (a US$800 option) and Sharp doesn't make PCL drivers for Linux or OS X for that printer.  Since then I've been using the generic PCL6 driver, but the quality is poor and only B&W.

My advice is to check your driver compatibility.

---

