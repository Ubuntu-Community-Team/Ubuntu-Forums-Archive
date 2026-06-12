---
title: "having trouble with &quot;terminal&quot;"
date: 2008-09-02
forum: General Help
---

### Post by itsguardianjon on 2008-09-02
sometime terminal will let me go "su" most of the time it wont saying authentication error and i know i have the right root password because there is only one.  what could i be doing wrong please help

---

### Post by mb_webguy on 2008-09-02
Well, you really shouldn't be using su, and root shouldn't have a password.  By default, the root account is locked, to you shouldn't be able to su into root at all unless you've done something to the account.

To issue a command with root privileges in Ubuntu, you should use sudo.  To run a GUI application with root privileges, you should use gksu or gksudo.

You might want to read [this]("https://help.ubuntu.com/community/RootSudo") for more information.

---

