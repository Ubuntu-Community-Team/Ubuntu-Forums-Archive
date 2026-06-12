---
title: "[SOLVED] firefox problem"
date: 2008-10-05
forum: General Help
---

### Post by suhaib1thariq on 2008-10-05
i had installed hardy ...by default it installed firefox 3 beta5..........i don't want to use beta edition....how can i remove it and use firefox3.03

---

### Post by jmszr on 2008-10-05
Have you run the update manager System>Administration>Update Manager? The update to Firefox 3.03 came through a week-ten days ago or so.

---

### Post by Kevbert on 2008-10-05
Do you have all your software sources enabled ?  With an active internet connection go to System-Administration-Software Sources. Enter your log-in password when prompted. Check under the Ubuntu Software tab that the top four boxes are ticked. Remove the tick from the CDROM box if ticked (stops prompt for CD every time you do an update).  Under the Update tab check that Important, Recommended and Unsupported (for restricted drivers) boxes are ticked.  You'll then be told that your software list is out of date, click on Reload to allow it to update.  Then click on Close.
Now open a terminal window via Applications-Accessories-Terminal.  Enter the following
```
sudo apt-get update
sudo apt-get upgrade
```
(enter your log-in password if prompted).
You'll probably find there's a lot of software to download...

---

### Post by suhaib1thariq on 2008-10-05
i had to change firefox 3 beta 5 to fire fox3.03....how can i do that....it upgrades all softwares

---

### Post by tonybaqain on 2008-10-05
goto System -> Administration -> Update Manager

click on check, and after it finishes deselect everything and just select anything concerning firefox and click ok and/or apply on each message displaying dependencies to the firefox like libc6-dev and xul-runner .....etc.

click on apply, and then it will update firefox only.

have fun :)

---

