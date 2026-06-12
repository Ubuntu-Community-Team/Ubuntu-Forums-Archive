---
title: "Help with limewire installation failure"
date: 2008-09-15
forum: General Help
---

### Post by Blakerx2 on 2008-09-15
I was installing limewire for linux and I clicked on cancel by accident now every time I try to re-install it it says:

Only one software management tool is allowed to run at the same time
Please close the other application e.g 'Update Manager", 'aptitude' or
Synaptic first. 

Well I have none of those open so I tried 2 open one and when I do this error comes up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I open the Terminal do the command dpkg --configure -a and it says:

requested operation requires superuser privilege, so I try to install the program 'super' with the command sudo apt-get install super, but everytime I do it says: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
So how can I fix the problem I have? Is there a way 2 debug my installation?

---

### Post by ronnielsen1 on 2008-09-15
Type this into a terminal. It will fix it.
[I][B]sudo  dpkg --configure -a

[/B][/I]Also recommend frostwire over limewire

---

### Post by quibbler on 2008-09-15
> **Blakerx2 said:**
> I was installing limewire for linux and I clicked on cancel by accident now every time I try to re-install it it says:

Only one software management tool is allowed to run at the same time
Please close the other application e.g 'Update Manager", 'aptitude' or
Synaptic first. 

Well I have none of those open so I tried 2 open one and when I do this error comes up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I open the Terminal do the command dpkg --configure -a and it says:

requested operation requires superuser privilege, so I try to install the program 'super' with the command sudo apt-get install super, but everytime I do it says: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
So how can I fix the problem I have? Is there a way 2 debug my installation?
Open the terminal and type:

sudo dpkg --configure -a

when asked type your password.
Read this to learn more about sudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards quibbler

---

### Post by Blakerx2 on 2008-09-15
i found the answer somewhere else and it was that command but on the root terminal.

---

