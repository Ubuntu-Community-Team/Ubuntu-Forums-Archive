---
title: "Printing Problem PSC1210"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by kewlman on 2006-07-23
i have an all in one HP PSC1210.. i installed the driver and everything without any problems. I goto print something it takes in the paper but doesn't do anything.. the activity light on the printer flashes and that is it.. i look into the printer manager and it says the print job is printing.. this is probably not a problem with ubuntu but i am sure someone here can help me out.. it's probably something stupid i am overlooking. thanks for the help.

Matthew Benedict

---

### Post by Sef on 2006-07-24
Are you able to print a test page?

---

### Post by kewlman on 2006-07-24
the test page doesn't print either.. the paper feeds in but then it stops with the activity light on the printer flashing.. i let it sit there for a long time but it never goes any farther. it shows it printing in the print manager.

---

### Post by Sef on 2006-07-24
I had problems with getting my PSC 1610 running under Breezy.  This is a slightly modified version of what I did to get it running.  (Thanks to wonderingjew for the original.)

```
sudo apttitude install hplip gtklp xpp python-qt3-doc libqt3-mt-mysql hplip-ppds
```

---

### Post by soliac on 2006-09-29
I have the same problem, but over an ethernet connection. I have an HP PSC 1210 connected to an XP box. I'm trying to print to it from my Ubuntu laptop via ethernet. Ubuntu sets up the printer all right but when I try to print anything the printer starts making noise then stops. XP says it's printing but NOTHING happens.
On XP the attempted print shows up in the queue - Right Click, Properties shows "Datatype: RAW". I think this may be the problem?

---

### Post by vliegje20 on 2007-02-06
I also have a problem with this printer. I installed it. But when i start tot print the printer goes printing but nothing appears on the paper. The papers are empty. How can i solve this?

---

### Post by rustybronco on 2007-03-12
I have the same problem with edgy eft when using hplip-1.7.2 it prints blank pages, This is not a printer problem the printer works under windows xp.

***EDIT*** don't use system>preferences>printers to set up your printer, use applications>acessories>hp it and name it psc-1210x or to something you can remember and make it the default (you may have to go back into printers in "system" and remove the existing one, that's the reason for the psc-1210x) it worked on mine last night.

---

