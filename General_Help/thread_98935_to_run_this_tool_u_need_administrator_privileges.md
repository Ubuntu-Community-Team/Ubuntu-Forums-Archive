---
title: "to run this tool u need administrator privileges"
date: 2005-12-04
forum: General Help
---

### Post by drewbek on 2005-12-04
This cums up after i try and run the network configuration tool but when i put in my root password it cums back as ""the enterd password is invalid . ANy help would be good

---

### Post by aysiu on 2005-12-04
Enter your sudo password, not the root one.
The first user you created during installation has sudo privileges.

---

### Post by az on 2005-12-04
[QUOTE=drewbek]This cums up after i try and run the network configuration tool but when i put in my root password it cums back as ""the enterd password is invalid . ANy help would be good[/QUOTE]
Ubuntu uses sudo for privilege escalation.  You should not have a root password on your system.  The Desktop is set up to use the user's password to gain root priviledges.

There is a wiki page about this at
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You can enable the root account if you wish, but it is better to avoid that.

Sudo has a lot of advantages including logging of all sudo commands.

---

