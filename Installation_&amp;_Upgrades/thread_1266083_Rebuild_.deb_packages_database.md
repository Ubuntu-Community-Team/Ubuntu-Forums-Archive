---
title: "Rebuild .deb packages database"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by zmdmw52 on 2009-09-14
[FONT=Arial]Is there a command (from the CLI) to rebuild the package database in Ubuntu - similar to the rpmdb --rebuilddb / rpm --rebuilddb for RPM-based systems (Fedora/openSUSE), as mentioned [here]("http://linuxpoison.blogspot.com/2007/10/repair-corrupt-rpm-database.html"): 
[http://linuxpoison.blogspot.com/2007/10/repair-corrupt-rpm-database.html](http://linuxpoison.blogspot.com/2007/10/repair-corrupt-rpm-database.html)

or for openSUSE at [this link]("http://en.opensuse.org/SDB:Speed_up_Package_Manager_Stack#Defragment_internally"):
[http://en.opensuse.org/SDB:Speed_up_Package_Manager_Stack#Defragment_internally](http://en.opensuse.org/SDB:Speed_up_Package_Manager_Stack#Defragment_internally)

> First backup and then delete by doing the following command:
$ su
 # cp /var/lib/rpm/__db.001 /home/nikesh
# rm /var/lib/rpm/__db.001
# cp /var/lib/rpm/__db.002 /home/nikesh
# rm /var/lib/rpm/ __db.002

[/FONT]      [FONT=Arial][COLOR=Blue]# **rpm –rebuilddb**[/COLOR][/FONT][FONT=Arial]  [/FONT]

---

