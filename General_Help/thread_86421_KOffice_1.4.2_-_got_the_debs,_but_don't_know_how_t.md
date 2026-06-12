---
title: "KOffice 1.4.2 - got the debs, but don't know how to install them"
date: 2005-11-05
forum: General Help
---

### Post by magnusbb on 2005-11-05
**Hello,**

I am not very familiar to the apt-get system. I have found the debs to the latest release of KOffice (1.4.2) and now I want to install them. Breezy features the 1.4.1 version, but some important fixes are provided in this latest version.

**Here's the link:**
[ftp://ftp.no.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu/pool-breezy/koffice](ftp://ftp.no.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu/pool-breezy/koffice)

**Other mirrors:**
[http://download.kde.org/download.php?url=stable/koffice-1.4.2/](http://download.kde.org/download.php?url=stable/koffice-1.4.2/)

Here are all the needed debs. But how to install them? There are many, and I would like to install them at once, not just one by one? Do you have any ideas on how to do this simple?

---

### Post by adwait on 2005-11-05
how about
```
sudo dpkg -i *.deb
```

---

### Post by magnusbb on 2005-11-05
Yeah, but that's one by one. I want them installed in a way like "apt-get install koffice". I am really not that advanced.

---

### Post by magnusbb on 2005-11-05
Solved.

I used the link,
[ftp://ftp.no.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu/](ftp://ftp.no.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu/)

and added

deb [ftp://ftp.no.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu/](ftp://ftp.no.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu/) breezy main

to /etc/apt/sources.list

Piece of cake, really.

---

