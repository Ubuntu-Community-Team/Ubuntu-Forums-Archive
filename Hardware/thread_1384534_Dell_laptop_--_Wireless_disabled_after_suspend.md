---
title: "Dell laptop -- Wireless disabled after suspend"
date: 2010-01-18
forum: Hardware
---

### Post by B_Nut on 2010-01-18
Hoping someone can help, this is getting very frustrating.

I recently upgraded a Dell D400 to Ubuntu 9.1, and that's come with a host of issues.  The worst one, which popped up recently, is that my onboard wireless is disabled after I wake the laptop up from suspend.  If I right click on the wireless icon in the panel "enable wireless" is unchecked and greyed out.  Restarting gets it working again, until I suspend.

A second, less important issue is that closing the laptop lid freezes the system instead of suspending.  This is not as important as the above issue, because I've gotten used to manually suspending before closing it, but if anyone has ideas for fixing that it would be great.

---

### Post by midnightsunray on 2010-01-20
I have the same exact problem, whenever I suspend I have to reboot in order to get wireless working; a simple "ifconfig eth1 down/up" won't work.  
Same problem when I push the "wifi on/off" hot key, while bluetooth switches without problems.
I have Ubuntu Karmic with 2.6.31-17 kernel, everything else is working just fine.
Hope to get it solved soon, in the meanwhile I wait for suggestions :)

---

### Post by TheAsarya on 2010-01-22
try this thread
[http://ubuntuforums.org/showthread.php?t=1383429]("http://ubuntuforums.org/showthread.php?t=1383429")

---

### Post by B_Nut on 2010-02-09
No, adding neither ndiswrapper or rt61pci to MODULES in /etc/default/acpi-support works.

In addition I still have the issue of the system freezing when I close the lid.

These are fairly recent problems, they didn't happen immediately after I upgraded to the new version, but some time later.  Very frustrating.  If anyone has any other ideas, I'll give them a shot.

---

