---
title: "updated ubuntu 8, lost monitor and graphics card"
date: 2008-10-20
forum: General Help
---

### Post by jebsector on 2008-10-20
Sorry to post, I upgraded recently with the latest updates, after rebooting it now says it can't properly configure my graphics card or monitor, and asks me to do it manually.  

I'm running an msi k9a2 cf motherboard, amd tri-core x64 processor, evga geforce graphics card, and standard lcd monitor.  When I built this thing, ubuntu ran fine after installing the graphics driver.  Did the os just lose the driver and I need to re-install it, or ?

Thanks, and sorry for the need to post..

---

### Post by ajmorris on 2008-10-20
hi there,
can you please post the output of:
 
```
sudo lspci
```
 
```
sudo glxinfo
```
 
and also the contents of your /etc/X11/xorg.conf file.
 
[quote=jebsector]
Thanks, and sorry for the need to post.. [/quote]
no need to be sorry :)
 
 
AJ

---

### Post by jebsector on 2008-10-20
sorry again, I ended up hosing the os, after I reinstalled the driver I can't boot into gnome.  I'm going to reinstall, update, and see what happens..

---

