---
title: "warnings from apt-get"
date: 2005-12-06
forum: General Help
---

### Post by sitara on 2005-12-06
I have run 'apt-get update' and get the following warnings:

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


what does it mean by 'stat' ? What should I do?

Thanks in advance

Keith

---

### Post by sitara on 2005-12-06
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by mlomker on 2005-12-06
[QUOTE=sitara]what does it mean by 'stat' ? What should I do?
[/QUOTE]

That just means 'file not found'.  Maybe a bad Internet connection or perhaps they were updating the repository when you tried to connect.  I'd just try again later or use one the [mirrors]("http://wiki.ubuntu.com/Archive") instead of the main repositories.

---

### Post by aysiu on 2005-12-06
You could also try the directions at the bottom of the page in the first link of my sig.

---

