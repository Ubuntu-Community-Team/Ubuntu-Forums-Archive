---
title: "accepting all encryption methods"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by vielmaj on 2009-06-16
I am moving from suse 11 to ubuntu 9.04 and my old /etc/shadow encrypted passwords are not working.  These old passwords are encrypted by blowfish and DES and ubuntu uses SHA512.  Is there any way I can still use my old passwords so I do not have to reset everyones passwords.

Thanks,

jason

---

### Post by jancelis on 2009-11-05
For the DES part I would set ENCRYPT_METHOD in /etc/login.defs to DES.
So the line in /etc/login.defs that says:
ENCRYPT_METHOD SHA512
should become:
ENCRYPT_METHOD DES

---

