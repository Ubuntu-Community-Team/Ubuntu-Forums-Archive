---
title: "Frozen drive and HDD changes"
date: 2015-09-21
forum: Hardware
---

### Post by graeme2 on 2015-09-21
I am trying to change hard drive setting with the following and after a reboot, shutdown or suspend it is still frozen. How do I unfreeze so I can disable as below please

"hdparm --security-disable PASSWORD /dev/sda"

---

### Post by tgalati4 on 2015-09-21
Welcome to the forums.  What is the make and model of the hard disk?  Some disks with a security password enabled are difficult to manage with *hdparm*.

What version of Ubuntu?  Did you set a password to lock the drive and now you are having trouble unlocking it?

> tgalati4@Mint17 ~ $ hdparm --security-help

ATA Security Commands:
 Most of these are VERY DANGEROUS and can destroy all of your data!
 Due to bugs in older Linux kernels, use of these commands may even
 trigger kernel segfaults or worse.  EXPERIMENT AT YOUR OWN RISK!

 --security-freeze           Freeze security settings until reset.

 --security-set-pass PASSWD  Lock drive, using password PASSWD:
                                  Use 'NULL' to set empty password.
                                  Drive gets locked if user-passwd is selected.
 --security-unlock   PASSWD  Unlock drive.
 --security-disable  PASSWD  Disable drive locking.
 --security-erase    PASSWD  Erase a (locked) drive.
 --security-erase-enhanced PASSWD   Enhanced-erase a (locked) drive.

 The above four commands may optionally be preceded by these options:
 --security-mode  LEVEL      Use LEVEL to select security level:
                                  h   high security (default).
                                  m   maximum security.
 --user-master    WHICH      Use WHICH to choose password type:
                                  u   user-password (default).
                                  m   master-password


---

### Post by graeme2 on 2015-09-21
Hey,
14.04 LTS and WD5003ABYZ. Enabled and no O/S found message so put in another server which took it. Trying to reset back. SED drive tho seems 1/3 of mine support it.
Many thanks

---

