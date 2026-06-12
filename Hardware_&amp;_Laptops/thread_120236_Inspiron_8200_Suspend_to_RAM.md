---
title: "Inspiron 8200 Suspend to RAM"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by stults on 2006-01-21
I am still a relative noob, so forgive me for asking a common question.  

First, here are my specs:
   Dell Inspiron 8200
   P4 1.6GHz~1.2GHz
   1GB RAM
   NVidia GeForce2 Go (32mb)
   Ubuntu Breezy (5.10) fully updated

I am trying to get suspend to ram working, but am having no luck.  When I close the lid it only locks the screen.  Opeing the lid brings up the password box.  

I have been looking forever for a solution, but haven't found one that suits my situation yet.  I have played with the /etc/default/acpi-support file to enable suspend to ram.  I have edited the /etc/acpi/events/lidbtn file to enact the sleep.sh script.  Done the howto guide for acpi susped to ram as suggested in several other threads, with no luck.  I don't want to hibernate to disk, just suspend.  Though if it helps, when I try to hibernate the system will not resume (blank screen).  

I have tried suspending through the logout menu and it does nothing.  This, to me, suggests a problem/conflict with the scripts in /etc/acpi.  If you have any suggestions please keep them simple or detailed enough for a noob to follow.

Oh, I do love everything else about Ubuntu.  It detected everything right off the bat, including my cisco aironet 350 mini-pci card.  Though I wish somebody would get off their ass and get wpa working without it being a pain the ass (still working on that).

---

### Post by stults on 2006-01-24
Thought I'd let anybody looking at this know that I resolved the issue.  My only explanation is that something I had installed broke the suspend.  More than likely it was the nvidia legacy drivers I got from the repositories.  I simply wiped it and started again with a fresh install.  Works great now with the "nv" driver.  Perhaps I'll try the "nvidia" driver sometime down the road again...

---

### Post by phillywize on 2006-12-28
Heh...we should start a support group.  My Inspiron 8200 with Dapper suspended/woke up nearly flawlessly with the howto at [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend").  I have almost the same rig as you:  1.7 ghz, 1 gb ram, nvidia geforce 2, and so forth.  I had a different wifi card though -- first a Dell TrueMobile 1150 (orinoco), and then an Intel jobbie of some flavor.    Now I have the same setup but upgraded to Edgy, and no luck.  Oh well.

Bob

---

