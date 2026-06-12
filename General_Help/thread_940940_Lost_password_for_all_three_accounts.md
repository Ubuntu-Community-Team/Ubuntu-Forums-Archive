---
title: "Lost password for all three accounts"
date: 2008-10-07
forum: General Help
---

### Post by SyntaxMage on 2008-10-07
Alright, my friend has been running Linux Ubuntu for a while now and has somehow lost the passwords for all three of her accounts. The root account hasn't been touched, but I'm pretty sure Hardy already has it shut off by default. Anyone have any suggestions on password recovery or how to log onto the accounts if we don't know the password?:confused:

---

### Post by Titan8990 on 2008-10-07
If no root password has been set then this can be done via recovery mode. Select recovery mode from the console. This will bring up the option to drop a root shell. From the root shell I would take the easy way out and just create a new user in the admin group:


adduser USERNAME admin

---

### Post by suhaib1thariq on 2008-10-07
try to load the ubuntu in memtest ....option next to default ubuntu in grub..

---

### Post by suhaib1thariq on 2008-10-07
try to load the ubuntu in memtest ....option next to default ubuntu in grub..recovery mode

---

### Post by aysiu on 2008-10-07
> **Titan8990 said:**
> If no root password has been set then this can be done via recovery mode. Select recovery mode from the console. This will bring up the option to drop a root shell. From the root shell I would take the easy way out and just create a new user in the admin group:


adduser USERNAME admin
That's basically how it works.

If you need more detailed instructions with screenshots, this may help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by matchstich on 2009-01-29
thanks for this, it worked for me

---

