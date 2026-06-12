---
title: "Fail to set time on boot"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2008-12-19
On my working system, during boot up, before the gui loads, a message pops up that it failed to set the time and date to whatever the current time and date is, however after the system is up and running the time and date are  indeed accurate.

I checked syslog to try and see where it is getting instruction to set the time on boot up and can't find it.

All i want to do is to stop the boot process from trying to set the time date, as it is getting set by gnome when the gui starts running.

---

### Post by markbuntu on 2008-12-19
Is your time coming from a internet time server?
Your system could be looking for the time server before your network is up.

---

### Post by upchucky on 2008-12-20
I am assuming that it is and that is why i need to find out where it is getting the command from to stop it from trying to set the time before the net is up.

syslog does not show where the file is that tells it to set the time on boot.

---

