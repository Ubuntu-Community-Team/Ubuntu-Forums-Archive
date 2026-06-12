---
title: "need some help"
date: 2008-07-20
forum: General Help
---

### Post by omlx2 on 2008-07-20
am trying to use the virtual box in ubuntu 
i did evreything corect at the end i got this msg
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

so any idea how to get permissions?!

---

### Post by Lori700698 on 2008-07-20
I just got ours running yesterday! Give everybody permission (systems, admin, groups) then you must log out then log back in and that's it.

---

### Post by sisco311 on 2008-07-20
```
sudo addgroup *username *vboxusers
```
replace *username* with your login name.

---

### Post by omlx2 on 2008-07-20
thanks 4 ur helps >>:guitar::)

---

