---
title: "HP printer disapeared."
date: 2014-04-29
forum: Hardware
---

### Post by ags40 on 2014-04-29
I have Kubuntu 14.04. Everything was perfect and all of a sudden I can not print. System settings says: "Print service is unavailable" "Bad file descriptor". Please help! Thanks

---

### Post by ajgreeny on 2014-04-29
Try uninstalling the printer (I'm not sure how in KDE or Kubuntu but presumably you will know) then reinstall it.  It may even be worth purging **hplip** and reinstalling that, assuming it is installed in Kubuntu.

---

### Post by tgalati4 on 2014-04-29
Since you are running 14.04 and updates will be coming in a steady stream, it helps to update your system first, then reinstall the printer.  If printing is important, then schedule your updates such that you have time to delete, reinstall the printer, and test the printer after applying the updates.  As 14.04 cures, the updates will slow down and your printer queue should fail less.

My experience is that kernel updates tend to cause CUPS failures including borking printer queues.

---

### Post by kc1di on 2014-04-29
When you say it diapered what exactly do you mean?  
is it not in the printer list anylonger?  go to system settings and printer if it's there delete and reinstall see if it will print.  I beleive in Kubuntu the only time the Icon shows in the task bar is when you activate a print job.

---

### Post by kc1di on 2014-04-29
When you say it diapered what exactly do you mean?  
is it not in the printer list anylonger?  go to system settings and printer if it's there delete and reinstall see if it will print.  I beleive in Kubuntu the only time the Icon shows in the task bar is when you activate a print job.

---

