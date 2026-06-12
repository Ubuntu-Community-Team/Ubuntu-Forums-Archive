---
title: "Help... how to start Ubuntu after changing the host OS"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by ranmeus on 2009-08-17
Hi, i am new here.
I had Vista on C:\ and installed Wubi and Ubuntu on D:\ and using the Vista bootloader to boot. Now i changed to windows 7 and it is somehow impossible to boot Ubuntu, which is still on D:\
It should be a common problem but i cant find the solution. Can anyone help me to resolve it?

Thank you guys in advance.

---

### Post by Mark Phelps on 2009-08-19
Wubi installs Ubuntu as if it were an MS Windows application even though you pointed it to a different partition.  Removing Vista removed access to Ubuntu, much the same as it removed access to any MS Windows programs you had installed, even if you pointed them to a different partition.

As far as I know, your only recourse would be to reinstall Ubuntu all over again -- and that is complicated by lots of problems that others have reported attempting to install Wubi through Windows 7.

---

### Post by ranmeus on 2009-08-19
Thank you!

Can i move it to another partition using  [LVPM]("http://lubi.sourceforge.net/lvpm.html")?

If there were no problem with Win7, can I rename the Disks folder, install a new Ubuntu, delete the new Disks folder and then change back the the old Disks folder?

---

### Post by Mark Phelps on 2009-08-20
> **ranmeus said:**
> Thank you!

Can i move it to another partition using  [LVPM]("http://lubi.sourceforge.net/lvpm.html")?
You can TRY to do that, but realize, that like with any other MS Windows app, there were undoubtedly registry entries created when Ubuntu was installed -- entries that now no longer exist.  Haven't tried the LVPM stuff, so I have no idea if it's able to recreate those registry entries.
>  If there were no problem with Win7, can I rename the Disks folder, install a new Ubuntu, delete the new Disks folder and then change back the the old Disks folder?
Don't know -- don't use Wubi, sorry.

---

