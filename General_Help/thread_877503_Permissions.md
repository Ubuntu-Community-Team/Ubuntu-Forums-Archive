---
title: "Permissions"
date: 2008-08-01
forum: General Help
---

### Post by PCessna on 2008-08-01
```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

```

Anyone help me set these permissions for VBox please :-)
I'm a bit confused

---

### Post by iaculallad on 2008-08-01
Add yourself to the vboxusers group:

Navigate to System->Administration->Users and Groups, click Manage Groups and
find the vboxusers group in the list, select it and click  on Properties.
In the users list find yourself and mark yourself as a member of vboxuers.
Click on OK button and log out of your account and log-back in.

---

### Post by PCessna on 2008-08-01
> **iaculallad said:**
> Add yourself to the vboxusers group:

Navigate to System->Administration->Users and Groups, click Manage Groups and
find the vboxusers group in the list, select it and click  on Properties.
In the users list find yourself and mark yourself as a member of vboxuers.
Click on OK button and log out of your account and log-back in.
Thanks for helping me through my quick brainfart :]

---

