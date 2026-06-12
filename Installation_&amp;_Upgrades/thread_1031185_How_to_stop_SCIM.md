---
title: "How to stop SCIM"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by theprolabi on 2009-01-05
Hello Guys 
How to stop SCIM "Smart Common Input Method"
it is a tool for language & keyboard support 
I just want to close it ,, i tried to kill it from system monitor but it reopened again  ,, 
case i cant open any kind of package management 
here is the problem when i tried to update the source list "sudo apt-get update" :-
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Even i cant run the update manager :confused:

any help please

---

### Post by ajgreeny on 2009-01-05
Make sure you have not got synaptic or update manager running when you use the ```
sudo apt-get update
``` command as it will be locked.  You can only have one application using the apt applications at any time.

---

