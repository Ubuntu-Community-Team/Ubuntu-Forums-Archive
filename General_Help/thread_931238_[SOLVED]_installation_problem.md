---
title: "[SOLVED] installation problem"
date: 2008-09-27
forum: General Help
---

### Post by suhaib1thariq on 2008-09-27
when i try to install any packages from net using sudo apt-get install <package name>        
 it is showing an error ...E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.



what's this error .....how can i sort this problem

---

### Post by DapperMe17 on 2008-09-27
OPen a terminal window & run that command. It will correct the error, which was likely due to an interrupted update.

You'll be able to continue after that.

You may have to type "sudo dpkg --configure -a"

---

