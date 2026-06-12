---
title: "relatively easy (i think) question on software installation"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by ddb13 on 2009-01-26
i have been trying to do installations of software and get the usual error message "dpkg was interrupted, you must manually run dpkg --configure -a and _cache->open() failed, please report.  when i run dpkg --configure -a i get the error message: dpkg: parse error, in file /var/lib/dpkg/updates/0147 near line 1: newline in field name #padding.  so i'm not sure what to do to resolve this and move on.  it happens to all be on a usb drive but it seems as though others have this same issue on normal installations.  any help appreciated.  thanks.

---

### Post by gettinoriginal on 2009-01-26
When this error message (dpkg was interrupted, you must manually run dpkg --configure -a and _cache->open() failed, please report) appears, it is because there is more than one package manager open at the same time.  You may not have terminal/synaptic/add remove or any combination open at the same time.  Only one.

---

### Post by ddb13 on 2009-01-26
i've restarted several times but nothing can install and i've only had one package manager open.  i have a feeling that one of the early update batches either didn't complete properly or something happened so that now nothing can update.  is there some way to undo the last update and try again?  thanks.

---

### Post by abn91c on 2009-01-26
make sure no package managers are open, in a terminal do sudo apt-get check
It may tell you what the problem is and suggest a command
Also try sudo dpkg --configure -a
followed by sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

---

### Post by ddb13 on 2009-01-27
i tried all of those and the only response i get is the same: dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem.  and of course when i run that i get the same error message (parse error) as above.  so it kind of goes around the same place.

---

### Post by abn91c on 2009-01-27
just make sure you use**[COLOR="Blue"] sudo[/COLOR]** in front of all the commands

---

