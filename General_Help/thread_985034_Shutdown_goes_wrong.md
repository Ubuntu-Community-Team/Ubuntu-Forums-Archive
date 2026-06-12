---
title: "Shutdown goes wrong"
date: 2008-11-17
forum: General Help
---

### Post by mariuszkopec on 2008-11-17
Recently I've noticed weird behavior of my computer, namely shutdown procedure doesn't work. Instead of switching the power of, the computer tries to reboot, but this also goes wrong: after showing some initial information (memory, drives etc.) but before entering grub, the computer displays something like "Searching the boot record on SCSI" and hangs. It happens only after shutdown (either from command line or by GUI). After reboot as well as after switching the machine on, everything is ok. The same effect I got with Fedora and Knoppix, but Microsoft Windows XP work ok (ie. switch the power off). I observed, that during this second (wrong) reboot the computer tries to read from CDROM, so I switched of booting from CDROM in bios, and now the only way is boot from SCSI (SATA is seen as SCSI), but it didn't change much. Any ideas what to do?

---

