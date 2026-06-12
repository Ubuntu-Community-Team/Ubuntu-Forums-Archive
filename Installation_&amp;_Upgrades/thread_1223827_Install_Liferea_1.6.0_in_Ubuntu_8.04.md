---
title: "Install Liferea 1.6.0 in Ubuntu 8.04"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by villalcalde84 on 2009-07-26
I like using Liferea, but the version in the repos is a bit old. Liferea v. 1.6.0 has been released and I would like to install it in Ubuntu 8.04.

I downloaded the source package from its website, extracted its content, but when I run ./configure in the terminal i get this: [http://paste.ubuntu.com/234069/]("http://paste.ubuntu.com/234069/")

How could I install the missing dependencies to install the latest version of Liferea?

Thanks!

---

### Post by villalcalde84 on 2009-07-26
Does anyone know how to install/upgrade this packages:
[LIST]
[*]gtk+-2.0 >= 2.16.0
[*]glib-2.0 >= 2.16.0
[*]pango >= 1.4.0
[*]gconf-2.0 >= 1.1.9
[*]libxml-2.0 >= 2.6.27
[*]libxslt >= 1.1.19
[*]sqlite3 >= 3.6.10
[*]gmodule-2.0 >= 2.0.0
[*]libglade-2.0 >= 2.0.0
[*]libsoup-2.4 >= 2.26.1
[*]webkit-1.0 >= 1.1.10
[/LIST]

in Ubuntu 8.04, so I can install Liferea 1.6.0?

Thanks.

---

### Post by AlexFera on 2009-07-28
You could try: sudo apt-get build-dep liferea , to solve all dependencies.

---

### Post by villalcalde84 on 2009-07-28
> **AlexFera said:**
> You could try: sudo apt-get build-dep liferea , to solve all dependencies.

Thanks AlexFera, but if a run sudo apt-get build-dep liferea, it will download the dependencies for the version in the repositories, which is v. 1.4.14, right?

I would like to install/upgrade the dependencies that I mentioned above to install Liferea v. 1.6.0. Is that possible in Ubuntu 8.04?

---

### Post by villalcalde84 on 2009-08-05
Any other ideas on how this can be done?

---

