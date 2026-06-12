---
title: "Dual Boot Can't Access Files"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by ve3pkc on 2009-09-12
I have dual boot WinXP & Ubuntu 9.04 installation. I changed the hard drive configuration to give more space to Ubuntu with Partition Magic and was not able to reboot. I should have known better. In any case when I run Ubuntu off the installation disk I can see my previous files under a drive symbol 10.1GB Media. They are all there and I would like to copy them to a USB stick and reinstall Ubuntu. Unfortunately I don't have access because of file permissions. How can I access these files?
Regards
 
ok solved my problem. Used live cd, used: sudo chmod 777 -R /to_myfiles.............this changed the permissions so I could copy them.

---

