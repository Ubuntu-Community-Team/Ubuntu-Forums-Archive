---
title: "Unable to mount more than 1 resource from windows"
date: 2008-08-12
forum: General Help
---

### Post by dxxvi on 2008-08-12
I want to mount 2 resources from the same windows machine. If I mount any 1 of them, there's no problem. If I mount one before and mount the 2nd without un-mounting the 1st, the error is:

mount error 11 = Resource temporarily unavailable
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

These are the 2 commands used to mount them

[COLOR="RoyalBlue"]sudo smbmount //172.18.132.15/proj /tmp/proj -o username=tdangvu,password=HangTruong,workgroup=pmi.corp,uid=hannah,gid=hannah,ro

sudo smbmount //172.18.132.15/java /home/hannah/java-host -o username=tdangvu,password=HangTruong,workgroup=pmi.corp,uid=hannah,gid=hannah[/COLOR]

What's the problem here?

Regards.

---

