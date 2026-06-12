---
title: "Prepare internatl Hard Drive to be external"
date: 2020-10-13
forum: Hardware
---

### Post by edbelize on 2020-10-13
Hi everyone. After a long absence my laptop is deteriorating quick I therefore want to be sure I will be able to use the Internal Hard Drive as External and Access Read Write all the files.

My question is relating to the current system password on Ubuntu and the future access to System Folders (Home, Desktop, Downloads, Documents etc) as an external drive from an hypothetical Ubuntu system.

Should I deactivate system password now ?

Thank you for help and support

---

### Post by yapidumoac on 2020-10-13
> Should I deactivate system password now ?

Would not apply to accessing the laptop harddrive on the new hypothetical Ubuntu system. You can take ownership of the files by logging in as root and executing the [LEFT][COLOR=#242729][FONT=Consolas]chown command on the external harddrive. To connect a laptop harddrive to a desktop computer you would need a Sata to USB Hard Drive Caddy.[/FONT][/COLOR][/LEFT]

---

### Post by TheFu on 2020-10-13
Before doing anything, make backups. At least 2 copies for anything you don't want to lose.

Often, when systems are "deteriorating", the prime cause of that is the storage beginning to fail. All storage fails at some point. Hopefully, it isn't when we are unprepared and is just a minor inconvenience.

In Ubuntu there are drive decryption passwords and login passwords. I don't know about anything else on a current Ubuntu install that would have a password by default. There are lots of addons like a password manager which would have a password or use 2FA.  Also, older installs have some other stuff that turned out to have problems during upgrades and migrations.

The system drive could have built-in encryption. That usually happens on enterprise laptops at an added cost. That would be tied to the HDD or it could be tied to the laptop TPM chip + HDD.  If that is the situation, accessing that storage is tied to the specific laptop. You'll need backups of the data.

---

### Post by edbelize on 2020-10-14
Thank you very much for help and support. I get it i think.

---

