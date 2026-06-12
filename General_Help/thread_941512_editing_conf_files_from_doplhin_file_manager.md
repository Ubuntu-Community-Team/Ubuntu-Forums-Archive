---
title: "editing conf files from doplhin file manager"
date: 2008-10-08
forum: General Help
---

### Post by Technofear on 2008-10-08
I have tried to edit conf files (from Dolphin file explorer using right-click open with...kwrite somesuch) and am unable to save them (I am logged into the first user I created - from which I can administer the system). 

To get around this I am forced to open a terminal, user SU, and then use VI (which I am not familiar with).

What am I missing - is there anyway to invoke the editor with root privs

Thanks

---

### Post by Pro-reason on 2008-10-08
System files must always be edited as root.  Being able to &#8220;administer the system&#8221; just means that you are allowed to use &#8220;sudo&#8221; to temporarily become root.

To start a [graphical application as root](http://www.psychocats.net/ubuntu/graphicalsudo), use &#8220;gksudo&#8221; on GNOME/Xfce and &#8220;kdesudo&#8221; on KDE.  You can generally leave off the &#8220;do&#8221; on the end.  For example:

```

kdesu dolphin
kdesu kwrite
kdesu gparted

```

---

### Post by Technofear on 2008-10-08
Brilliant...Thanks....

---

