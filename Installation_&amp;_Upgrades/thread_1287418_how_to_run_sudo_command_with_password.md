---
title: "how to run sudo command with password"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-10
I want to run sudo command along with the password in one line.


Please help ..............:(

---

### Post by alienclone on 2009-10-10
i dont think it is possible because the password would be in plain visible text which would be a security risk.

i will get yelled at for this, but if you dont like having to type in the password at prompt then do a search for info on running as root permanently.

---

### Post by kerry_s on 2009-10-10
> **vksingh said:**
> I want to run sudo command along with the password in one line.


Please help ..............:(

why just use the nopasswd in visudo.
example:
you ALL=NOPASSWD: /path/to/your/command

i use a few.see pic

---

