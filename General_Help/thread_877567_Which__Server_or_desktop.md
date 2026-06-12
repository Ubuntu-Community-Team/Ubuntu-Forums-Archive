---
title: "Which:  Server or desktop?"
date: 2008-08-01
forum: General Help
---

### Post by rbstern on 2008-08-01
I'm experimenting with 8.04.1, both server and desktop.  The machine in question needs to support the following functions in a small home office:

- Samba (file sharing on two disks configured as RAID 1)
- Nagios remote server monitoring (requires Apache)
- SSH client

I'd also like to have the desktop interface to experiment with.

Would you recommend I install a desktop interface on top of the server, or should I install the desktop and add the above functionality?

Thanks in advance for any tips or insights.

---

### Post by p_quarles on 2008-08-02
It doesn't really matter, as you will wind up with the same thing which ever order in which you do it.

---

### Post by Locutus_of_Borg on 2008-08-02
if you want a minimal set-up e.g. you do not need all of the extra "stuff" the desktop edition of ubuntu includes, then go with the server install

---

### Post by Oldsoldier2003 on 2008-08-02
> **p_quarles said:**
> It doesn't really matter, as you will wind up with the same thing which ever order in which you do it.

Agreed. the only real difference is in the server kernel, which won't make much difference for the average user. If I were going to build a server that was going to see heavy loads I'd go with the server install and forgo the gui.

---

### Post by rbstern on 2008-08-02
Thanks, all.  I went with the server, just adding in what I need.

---

