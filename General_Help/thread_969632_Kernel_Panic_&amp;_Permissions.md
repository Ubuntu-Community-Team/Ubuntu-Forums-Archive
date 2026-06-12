---
title: "Kernel Panic &amp; Permissions"
date: 2008-11-03
forum: General Help
---

### Post by Elessor on 2008-11-03
Hi All,

Intel D945GCLF2 - Atom - 2GB Ram (tested & 100%)
Just tried update from 8.04 to 8.10 last night and now can't boot.

Get this final ominus message after a long list . . .
"Kernel Panic - Not Syncing: Attempted to Kill Init!"

Have researched and not discovered a solution so I'd like to do a fresh install, but I'd like to backup the files first.

Using a Live Session I can see the files but don't "have" the required "permission" to copu them.

How can I do it?

Thanks

---

### Post by dracayr on 2008-11-03
generally you can get the permissions by entering ```
gksudo nautilus
``` into a terminal. But You don't have to backup all your system. Only backup /home or, if your System has only one user (besides the deactivated root user), /home/username. But if you do this with the file browser, press crtl+H before copying to make hidden (configuration) files visible. Also, if you tweaked some configuration files (for example xorg.conf or menu.lst), back those ub too.

dracayr

---

### Post by azazell on 2008-12-08
I had the same issue until i updated the bios dowloanding the iso of the new version from here: [http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2926&OSFullname=OS+Independent&lang=eng&strOSs=38](http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2926&OSFullname=OS+Independent&lang=eng&strOSs=38)

---

### Post by JRV on 2008-12-14
> **azazell said:**
> I had the same issue until i updated the bios dowloanding the iso of the new version from here: [http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2926&OSFullname=OS+Independent&lang=eng&strOSs=38](http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2926&OSFullname=OS+Independent&lang=eng&strOSs=38)

Thankyou that helped a lot, now if only I can get the s-video to work.

---

