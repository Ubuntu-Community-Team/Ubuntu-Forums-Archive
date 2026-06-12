---
title: "Login without username &amp; password"
date: 2008-09-14
forum: General Help
---

### Post by amin_inb on 2008-09-14
Hi,

I want to log to my ubuntu (Command Line Interface no kde or gnome,..) without ask for username and password

is there any way to set some user as default one

---

### Post by Neo_The_User on 2008-09-14
Yes.

Go to System > Administration > Login Window > Security > Enable Automatic login.

I'm actually going to do the same thing. Thank you for the idea!

---

### Post by cariboo on 2008-09-14
No there is no way to login with no username and password from the command line. Unless you start up in recovery mode, then you are logged in as root, which is a dangerous way to run and should only be used to repair problems.

Jim

---

### Post by lswb on 2008-09-14
If your not concerned with the security implications, you could try putting this line in the file /etc/rc.local

su -l username

---

### Post by Sycron on 2008-09-14
Nice! It just works.

---

