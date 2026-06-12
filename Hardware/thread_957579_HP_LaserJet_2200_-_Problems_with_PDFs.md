---
title: "HP LaserJet 2200 - Problems with PDFs"
date: 2008-10-24
forum: Hardware
---

### Post by zenzike on 2008-10-24
I am using Ubuntu 8.10, and having troubles with my HP LaserJet 2200.

The printer was automatically detected and installed by the system. Printing documents from openoffice works fine.

However, when I try to print a PDF or PS, the printer does not work.

It might be that this printer has only 8MB of RAM, and yet the printer driver sets the printer as having 8-15MB of RAM. 

Someone else seems to have had the same problem [1], but I was unable to post on that thread since it was closed.

Does anybody have any suggestions? 

[1] [http://ubuntuforums.org/showthread.php?t=635770](http://ubuntuforums.org/showthread.php?t=635770)

---

### Post by cariboo on 2008-10-24
How did   you set your printer up? did you use the hplip setup utility? You may want to try some of the different printer driver files that are available through System-->Administration-->Printing.

Jim

---

### Post by zenzike on 2008-11-08
I tried various printing setup methods including hplip.

I have found out that the printer driver is just incredibly slow when printing anything complicated, like pdfs that are made 4 to a page and duplexed (which took about 20 - 25 minutes per sheet).

I'm wondering if this is because it's an old printer, or if it's the drivers that are causing bottlenecks.

---

### Post by mattman on 2008-11-30
I am having this problem also. I I ahve been trying to print a 48 page pdf and it fails everytime. Other single page documents seem to print fine. I will check the cups error logs and post back here later.

---

### Post by zenzike on 2008-12-01
A temporary solution seems to be using acroread to print certain PDFs -- make sure you enable the memory saving options.

Unfortunately, acroread can't actually print every file, some come out as garbage, but come out normally with evince.

---

### Post by mattman on 2008-12-01
I tried both evince and acroread. Maybe I'll try acroread in WinXP in virtualbox.

---

### Post by mattman on 2008-12-01
This worked fine. I guess this will have to be my last resort for printing pdfs for now. At least I don't have to reboot or print from someone elses computer.:)

> **mattman said:**
> I tried both evince and acroread. Maybe I'll try acroread in WinXP in virtualbox.

---

