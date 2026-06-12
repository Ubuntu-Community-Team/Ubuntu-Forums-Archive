---
title: "noob - root password"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Tsu on 2009-07-15
For some strange reason I was not asked to set the root password on installation.

I am unable to su root directly.

I must type "sudo su root"

May I ask why this is?

---

### Post by scorp123 on 2009-07-15
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wojox on 2009-07-15
Security

Check this link out:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mcduck on 2009-07-15
> **Tsu said:**
> For some strange reason I was not asked to set the root password on installation.

I am unable to su root directly.

I must type "sudo su root"

May I ask why this is?

Ubuntu doesn't use the root count directly, instead admin tasks are handled by using "sudo" to temporarily gain root permissions. The root account itself is locked and there is no password for it.

If you want to start a root session in a terminal, use "sudo -i" instead of "su".

The links posted in previous messages explain this in more detail, so be sure to read at least the rootsudo document.

---

### Post by scorp123 on 2009-07-17
> **robert3242 said:**
> Another option would be to run, (deleted command) ...  You're in violation of the forum rules. You might want to read up on those again.

---

