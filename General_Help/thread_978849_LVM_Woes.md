---
title: "LVM Woes"
date: 2008-11-11
forum: General Help
---

### Post by smah77 on 2008-11-11
I have two 200gb drives, one of which is always underused, and so I thought, "hey, self!  Let's give that LVM deal a shot!"  So I installed Interpid on an LVM-formatted drive, leaving the other drive as a normal ext3 drive (because I had to move data around).  I finally got around to formatting the second drive as an LVM drive, and merging the two.  Now I have problems.

1.  Every time I boot now I have to run vgscan --mknodes and then mount /home manually.  I didn't have to do this until I merged the two drives.

2.  Although the graphical LVM manager (system-config-lvm) shows my /home as 372.38gb, which is what it should be, nautilus doesn't register the free space as present.

Any tips, y'all?

---

### Post by smah77 on 2008-11-18
Really?  Nobody?

---

### Post by _sAm_ on 2008-11-18
I have never used "system-config-lvm", I know its brand new for Ubuntu 8.10, coming from Fedora. 

> and merging the two
Did you increase the filsystem you use on LVM as well?

---

### Post by smah77 on 2008-11-18
> **_sAm_ said:**
> I have never used "system-config-lvm", I know its brand new for Ubuntu 8.10, coming from Fedora. 


Did you increase the filsystem you use on LVM as well?

I think system-config-lvm does all that for you?  Though, maybe not.  It seemed to.

---

