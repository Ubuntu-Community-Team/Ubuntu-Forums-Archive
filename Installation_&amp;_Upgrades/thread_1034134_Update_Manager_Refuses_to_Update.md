---
title: "Update Manager Refuses to Update"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by PCHome on 2009-01-08
On Ubuntu 8.10, kernel 2.6.27-9 Gnome 2.24.1, suddenly the update manager is giving errors. There are two updates but they will not install:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run sudo dpkg --configure -a

it also gives an error:

> dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

It says to report but does not say where to report. Hopefully this is the right place. Any ideas?

Don

---

### Post by gettinoriginal on 2009-01-08
Do you have synaptic or terminal open when you are trying these updates ??  If so, close them then run update manager.

---

### Post by PCHome on 2009-01-08
No, nothing at all was open.

---

### Post by sendblink23 on 2009-01-08
> **PCHome said:**
> No, nothing at all was open.



Can  you    BOOT.. from the Past  Grub list   Kernel (ubuntu)...  before that update?


If you can.. then  once you enter it...   Re  click  ..  Update Manage, from the Older  Kernel (ubuntu)

---

### Post by kranny on 2009-01-08
Try downgrading the packages in aptitude...It may help

list the packages on your system that are not completely installed.From a command line terminal, you can enter the following:

sudo dpkg -l | grep -v ^ii

try unistalling them and then sudo dpkf --configure -a

---

### Post by PCHome on 2009-01-08
Oddly, the two packages seemed to install this morning after several failed attempts throughout the day yesterday! There was one error that some process was deferred until after a reboot but otherwise the system is no longer telling me that there are updates. Thanks all for the help!

Don

---

### Post by PCHome on 2009-01-08
Oops! I spoke too soon. Although no updates are showing now, when I open the Synaptic Package Manager, it pops up with the same error message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by PCHome on 2009-01-08
After a reboot, I was able to open the Synaptic Package Manager without errors but as soon as I tried to install something, the same error returned. There was a System Crash popup that said to report the problem but pressing the Report Problem button took me to a non-existent page. The error says:

> Package problem

Sorry, the package "cups 1.3.9-2ubuntu6" failed to install or upgrade.

---

### Post by PCHome on 2009-01-14
I'm still getting these errors and cannot install or uninstall anything at the moment. Please advise ASAP. Thanks!

---

### Post by Darth Kosik on 2009-01-14
I don't want to insult anyone or sound like a know-it-all or,(I'm the farthest thing from it)but did you open terminal? I didn't read all the posts, so please don't lash out at me.

---

### Post by PCHome on 2009-01-14
The error message said to open terminal to run a command that is supposed to fix the problem but it gives its own error when run. I did not have terminal open when trying to install anything, though.

---

### Post by Partyboi2 on 2009-01-14
I had this same problem the other day when upgrading cups, the way I got around it was to uninstall cups and cups-client then reinstall them plus any packages they removed.

---

### Post by PCHome on 2009-01-14
As far as I know, I wasn't doing anything with cups when the problem began and now I cannot run the installer to uninstall anything. I am not sure how to do it from the command line either.

---

