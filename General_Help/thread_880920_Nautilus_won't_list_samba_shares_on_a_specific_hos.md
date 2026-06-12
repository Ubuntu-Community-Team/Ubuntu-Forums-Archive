---
title: "Nautilus won't list samba shares on a specific host"
date: 2008-08-05
forum: General Help
---

### Post by retrovertigo on 2008-08-05
My workstation is running Ubuntu Hardy, however our main fileserver at work runs Windoze.  Using Konqueror I can easily type in **smb://hostname** and get a list of all the shares on that host.  However, with Nautilus I am not seeing any shares listed.  I checked the preferences and didn't see anything that jumped out at me, so is this something that Nautilus just can't do?  I know many of the shares that I need to access by heart, but it would still be nice to get a listing of them that I could select from within Nautilus, rather than typing out **smb://hostname/share**.

---

### Post by quazi on 2008-08-05
I'd also like an answer for this.  Installing printers (LPD) is particularly excruciating, with me needing to log onto a Windows machine to find the printer name.

---

### Post by motin on 2008-08-20
This is a bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903)

Use smb4k or konqueror as a work around...

---

### Post by noletolucas on 2008-09-03
> **motin said:**
> This is a bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903)

Use smb4k or konqueror as a work around...

same issue here, only able to list shares after installing smb4k. 

this bug was reported 2008-06-02 and has a low priority, anyone knows how long does it take on average to get fixed?

~~luky

---

