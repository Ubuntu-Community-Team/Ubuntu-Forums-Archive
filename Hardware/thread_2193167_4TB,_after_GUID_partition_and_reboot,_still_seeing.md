---
title: "4TB, after GUID partition and reboot, still seeing as 2TB???"
date: 2013-12-11
forum: Hardware
---

### Post by grandrigo on 2013-12-11
So reading different forums, I found out that the partitioning scheme Master Boot Record only supports 2TB. Well, I repartitioned my disk using GUID but still I see only 2.2TB ??? Any suggestions?
I also tried using OSX, and it successfuly partitioned it to 4TB but when I connected to th eother Ubuntu machine, it reads it as 2.2TB :/

Could that be a BIOS problem? I upgraded the bios as well....any help?

---

### Post by oldfred on 2013-12-11
Is this an internal or external drive. Besides older BIOS that may not support over 2GiB, some external drive enclosures also do not work with large drives.

What does gdisk show. Change example from sdb if that is not your drive.
sudo apt-get install gdisk
       sudo gdisk -l /dev/sdb

      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

