---
title: "Printing to Samsung scx-4825fn no longer works after upgrade to 12.04"
date: 2012-05-04
forum: Hardware
---

### Post by ub40d on 2012-05-04
I have a Samsung scx-4825fn for which I installed the Samsung unified driver in 11.10.

Ever since updating to 12.04, I can no longer print. In "document print status", jobs appear stopped. With "view attributes", the "job-printer-state-message" says "/usr/lib/cups/filter/rastertosamsungspl failed". Googling for that gave no useful hints.

In /etc/cups/cupsd.conf I raised LogLevel from warn to debug2. The only extra info I gathered that way is along the lines of "PID 7982 (/usr/lib/cups/filter/rastertosamsungspl) crashed on signal 11." which just means segmentation fault. I still have no clue why, much less how to get it back to a working state.

Help most welcome!

---

### Post by prshah on 2012-05-04
> **ub40d said:**
> Ever since updating to 12.04, I can no longer print. In "document print status", jobs appear stopped. With "view attributes", the "job-printer-state-message" says "/usr/lib/cups/filter/rastertosamsungspl failed". Googling for that gave no useful hints.


Hello, I was in much the same position with Samsung ML1676. I had to delete and re/add the printer using CUPS ([http://localhost:631](http://localhost:631)). All working fine now. Also had to do so with an Epson Stylux C210 <?> inkjet printer.

All settings and files remained the same, however, I suspect there was a PPD update somewhere during the upgrade. I did not have to delete/copy or move any files around.

Please make a note of your settings BEFORE you delete the printer from CUPS.

---

### Post by ub40d on 2012-05-05
> **prshah said:**
> Hello, I was in much the same position with Samsung ML1676. I had to delete and re/add the printer using CUPS ([http://localhost:631](http://localhost:631)). All working fine now.

Thanks. Just tried that. In CUPS I deleted the printer, then added it again; then printed a test page and got a dialog box

System program problem detected
Do you want to report the problem now? cancel / report problem.
Clicked on report problem and got another box
Sorry, ubuntu 12.04 has experienced an internal error.

I clicked show details and got another box:
invalid problem report: could not determine the package or source package name
In the second box, meanwhile, it said: executablepath /usr/lib/cups/filter/rastertosamsungspl

And in cups itself, the status for the job was:
stopped 
"/usr/lib/cups/filter/rastertosamsungspl failed"

So it all looks just as bad as before.

---

### Post by prshah on 2012-05-06
> **ub40d said:**
> System program problem detected
Do you want to report the problem now? cancel / report problem.

Hah, I'm getting the same error: See [http://ubuntuforums.org/showthread.php?t=1971928](http://ubuntuforums.org/showthread.php?t=1971928)

Never thought to connect it with CUPS, though. My printing works though; did you restart the CUPS service after fiddling with the printer? ```
sudo service cups restart
```

I will post back in this thread if I get any more info.

---

