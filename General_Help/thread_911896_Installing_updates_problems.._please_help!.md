---
title: "Installing updates problems.. please help!"
date: 2008-09-06
forum: General Help
---

### Post by dan1972 on 2008-09-06
Hi all from newbie to Linux.....

After automatic notification of avail updates are run, the following error message is displayed:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I try to run 'dpkg --configure -a' I'm told I have require "superuser privilege" to run this operation.

How can I fix this?  As a newbie to Linux/Ubuntu?

TIA

---

### Post by Bucky Ball on 2008-09-06
Type sudo first like this in a terminal:

**sudo dpkg --configure -a**

su = super user: do = do. Super user do! 

You'll find that a lot of commands that can screw up your machine and otherwise must be run with sudo first. You go **sudo su** and become root, but that is not a good idea. Just become it when you need to with 'sudo'. :)

---

### Post by gjoellee on 2008-09-06
go to Applications->Accessories->Terminal

enter the codes below
```
sudo su
```then enter your password, now add this code
```
dpkg --configure -a
```that should be it :)

---

### Post by dan1972 on 2008-09-06
Thanks - that worked a treat.  Appreciate your help...I think this is why Linux is gaining ground..

---

### Post by Bucky Ball on 2008-09-06
No probs. Post again with any other questions and welcome. :)

---

