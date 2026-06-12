---
title: "Fresh install with existing LVM"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by sugargenius on 2008-12-12
Planning to do a fresh 8.04 server install on a box that has existing 4 drives under lvm.  Will installer detect this and incorporate existing vg and lg?

---

### Post by sugargenius on 2008-12-16
***bump***
Anybody?

---

### Post by yknivag on 2008-12-17
I can't answer your question, I'm afriad, but have a very similar problem!

My OS and "/", "/home" and "/swap" all reside on a single physical disk in normal partitions, but I have a large RAID5 array (1.5TB) on which I intend to put 3 LVs (to increase flexibility and quotaring).

My issue is that if I lose the OS disk (or wish to install a new OS) will this recognise the LVs and allow me to mount them (as I would be able to do with ordinary partitions) or would I need to "export" the LVs first and them "import" them to the new system? (OK for a planned upgrade but not so convenient in a crash/disk loss system!)

Would welcome any comments...

---

### Post by sugargenius on 2008-12-18
I haven't done it yet, but I think it can be accomplished with these commands:
vgchange
vgexport
vgimport

[http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)

---

### Post by yknivag on 2008-12-21
That's my worry - that it can (seemingly) only be done by using vgexport and vgimport.

What if the main system becomes irrecoverable, to the point where it is not possible to run vgexport? Will a fresh install still recognise my volumes and my data?

---

### Post by keithweddell on 2008-12-21
This can be done by the installer if you use the alternate installation disk. Partition manually and you can activate the LVM and choose where to mount the partitions and whether or not to format partitions. I  clean install each new release by this method and keep my home and data partitions intact.  Courage.

Keith

Keith

---

### Post by sugargenius on 2008-12-23
Do you have to do anything to the LVM prior to doing the new install (ie vgchange or vgexport?)

---

### Post by keithweddell on 2008-12-23
Nope.  The installer will do it all for you.

Keith

---

### Post by finneyabraham on 2009-03-31
I had an Logical Volume under openSUSE 11.1 comprising 5 500GB disks. My / and home partitions were on a seperate disk. On this disk, I did a clean install of Ubuntu 8.10. Now I cannot see or access my LVM.

Please help.

---

