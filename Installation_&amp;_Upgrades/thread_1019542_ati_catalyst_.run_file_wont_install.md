---
title: "ati catalyst .run file wont install"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by derran on 2008-12-23
Can some one please help me I am new to ubuntu. I cannot install the catalyst run file it keeps telling me to install as super user. I checked that box under permisions and it still fails I even ran it as sudu command in terminal but it still gives me same message.

---

### Post by taurus on 2008-12-23
Install it from a terminal.

Make sure it is what you want to install since there is no uninstall (that I know of) once you've installed it.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod +x filename.run
sudo ./filename.run
```
Assuming that file, filename.run, is on your desktop.

---

### Post by derran on 2008-12-23
Thanks its working

---

### Post by AlmightyMokona on 2011-06-30
Hey btw Derran, remember if this happens with another program you are trying to install, you can always access your user account privileges in **System Settings** > **Users and Groups**. Cheers!

---

