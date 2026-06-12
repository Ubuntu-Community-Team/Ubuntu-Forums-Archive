---
title: "No Sound At All - no changes, just No Sound"
date: 2008-10-26
forum: General Help
---

### Post by RogerDavis on 2008-10-26
Today I noticed that I have no sound AT ALL, at any time, in any program, nor system sounds.  If I reboot in Windows XP, no problems.  Come back to Ubuntu, no sound at all.

I can't find any settings that could turn off sound that are set wrong, everything looks fine, I just can't hear anything.  I must be missing something?!?

---

### Post by RogerDavis on 2008-10-26
Additional info :
Since this started earlier today, the systems has failed to find the boot disk once, and twice failed to shut down properly, I had to turn the switch off.

---

### Post by alecjw on 2008-10-26
Run the command "groups" sans quotes in the terminal and tell me what it says

---

### Post by RogerDavis on 2008-10-27
As you requested :
------------------------------------------------
root@Roger-Ubuntu-desktop:/home/roger# groups
root
root@Roger-Ubuntu-desktop:/home/roger# 
----------------------------------------------------
Thanks!

---

### Post by alecjw on 2008-10-27
You shouldnt be logged on as root...

---

### Post by RogerDavis on 2008-10-27
OK, but does this have any affect on fixing the sound problem?  This might be because I used root terminal to do this?
Thanks!

---

### Post by alecjw on 2008-10-27
Run that command again as yourself.

---

### Post by RogerDavis on 2008-10-28
roger@Roger-Ubuntu-desktop:~$ groups
roger adm dialout fax cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin
roger@Roger-Ubuntu-desktop:~$ 

Thanks!

---

### Post by alecjw on 2008-10-28
Ah right... My idea was wrong then...
I though you might not have been a member of the "audio" group (required to use audio devices)

---

