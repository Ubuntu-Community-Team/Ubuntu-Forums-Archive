---
title: "[SOLVED] Trying to transfer from Wubi to dual boot, problems installing partition man"
date: 2008-10-29
forum: General Help
---

### Post by supwest on 2008-10-29
I'm trying to switch from Wubi to a dual boot. I've got the Wubi installation on a 70GB HD, and I'd like to give the whole disk over to Ubuntu. I've read the tutorial on using LVPM [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) but I'm having problems installing the partition manager as listed in the tutorial. 

I downloaded it from the link given, [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821),and when I rebooted and tried to boot the partition manager I got this message

> Booting 'UNetbootin-partitionmanagerrev146'
root (hd7,)

Error 21: Selected disk does not exist

Then I downloaded it again, and tried to reinstall, and now the installation fails.

> Failed to install package 'unetbootin_partitionmanagerrev146_all.deb'

and in the Terminal output is

> (Reading database ... 116234 files and directories currently installed.)
Preparing to replace unetbootin partitionmanagerrev146 (using .../unetbootin_partitionmanagerrev146_all.deb) ...
Unpacking replacement unetbootin ...
Setting up unetbootin (partitionmanagerrev146) ...
expr: syntax error

I think I might not have the most recent version of the partition manager. Would that have something to do with this?

Thanks

---

