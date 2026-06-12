---
title: "Restoring System Permissions"
date: 2008-08-06
forum: General Help
---

### Post by omara.mike@gmail.com on 2008-08-06
Hello, made a major blunder on my system.  I was logged in as root and issued "chmod 777 -R" at /.   I was not quite sure of my location when I issued the command.  Anyway my system is completely hosed.  I can't do anything but log in.  No sudo, no su -.
==============
Is there anyway possible to restore my Permissions on my system to what they were?

Kind regards,
Linux wantabee:confused:

---

### Post by mrsteveman1 on 2008-08-06
I'm not much help i suppose, but i do think Suse has a system that keeps track of the permissions on specific files and enforces them or corrects them when they change, perhaps Ubuntu at least has a file with the permissions in it?

Best bet really is to backup whatever you can and reinstall, you can use a livecd and an external disk to do it and it will save you the time of screwing with permissions problems.

---

### Post by Yannick Le Saint kyncani on 2008-08-06
> **omara.mike@gmail.com said:**
> Is there anyway possible to restore my Permissions on my system to what they were?

Nope, either restore a backup or reinstall.

---

### Post by lswb on 2008-08-06
After booting up in recovery mode, you could try the command

dpkg-reconfigure -a

This will take quite a while to complete as it will attempt to reconfigure every installed package on your system. Directories and files not directly created by package installation won't be changed.

---

### Post by mrsteveman1 on 2008-08-06
> **lswb said:**
> After booting up in recovery mode, you could try the command

dpkg-reconfigure -a

This will take quite a while to complete as it will attempt to reconfigure every installed package on your system. Directories and files not directly created by package installation won't be changed.

Yea but will that actually go through and check permissions? I thought it only ran post-installation scripts?

---

### Post by omara.mike@gmail.com on 2008-08-07
Thanks for the replies:
For giggles I tried dpkg-reconfigure -a just because I have no 
idea what else to try.  It did not work.
==============
If I was to backup and try to reinstall how would I know exactly what to back up? And wouldn't my permission be screwed on these files as well?

Regards,
Mike

---

### Post by omara.mike@gmail.com on 2008-08-09
I went ahead and rebuilt my system.

Thank you.

---

### Post by Elfy on 2008-08-09
In reply to your > If I was to backup and try to reinstall how would I know exactly what to back up? you would just backup your home - or at least the stuff you really couldn't get away with and you should be able to restore those permissions.

If your username is your real address I would ask a mod/admin to see if you can change your username as you could quite likely open yourself up to all sorts of trouble from bots. Put a post in forum feedback if you feel it's necessary.

---

