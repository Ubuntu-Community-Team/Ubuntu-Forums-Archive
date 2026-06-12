---
title: "New Brother Laser printer won't work with Opera 64 Browser"
date: 2019-11-24
forum: Hardware
---

### Post by cybrsaylr on 2019-11-24
Have Opera Version:64.0.3417.92, Opera is up to date.
Got a new Brother laser printer HL-L 2390DW.
Installed it with Windows 10 and it runs fine.

Installed Brother printer on my desktop running Ubuntu 18.04.3 LTS and it runs, scans, copies fine using Firefox, Chrome and Vivaldi browsers but can't get it to work with Opera Version:64.0.3417.92.

Help.
What needs to be done to get this Brother laser printer working with Opera 64?

---

### Post by deadflowr on 2019-11-24
Opera 64.3417.92 is the snap version.
Might need to connect to the cups interface
Try
```
snap connect opera:cups-control
```

---

### Post by him610 on 2019-11-24
Does your Brother HL-L2390DW print, scan, and copy using the available applications in Ubuntu 18.94.3 like OpenOffice or any of the text editors? If so, then your issue is with Opera. I do not use Opera; however, you might be better served by asking in an Opera forum.

---

### Post by cybrsaylr on 2019-11-24
deadflowr

Put in code: snap connect opera:cups-control, and it seems to work now! 

Thanks


him610 

Did ask on Opera forum earlier but got no response as yet.
Have found Ubuntu forums more helpful over the years.

Did print out a page using LibreOffice which looked OK but needs some adjusting.
This new Brother laser printer does much more than older printers.

---

