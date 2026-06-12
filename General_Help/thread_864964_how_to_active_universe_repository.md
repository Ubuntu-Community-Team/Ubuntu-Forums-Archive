---
title: "how to active universe repository"
date: 2008-07-20
forum: General Help
---

### Post by rafiqasad on 2008-07-20
I want to install the VLC player but i don't know how to activate the universal repository. Please some one help and guide me

---

### Post by ibutho on 2008-07-20
You can run ALT-F2, enter the command to run as "gksudo gedit" (without quotes). When gedit runs, go to the /etc/apt directory and open a file called sources.list. Remove the # in fron't of any lines that have the word "universe". After that close gedit, update your software sources and install VLC. Another option would be to run the ADD/Remove program and somewhere in the menu, there is an option to show all software sources.

---

### Post by cpetercarter on 2008-07-20
System > Administration > Software Sources

Check "Community maintained open source software (universe)"

---

### Post by PmDematagoda on 2008-07-20
Or you can open Software Sources in System>Administration>Software Sources and then tick the Universe repository in the Ubuntu Software tab.

---

