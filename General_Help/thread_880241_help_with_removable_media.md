---
title: "help with removable media"
date: 2008-08-04
forum: General Help
---

### Post by jon9314 on 2008-08-04
i have three users on my computer if more than one is logged in and the active user plugs in a thumb drive when we switch users there is a window for the drive but it has the other users permissions. how can i keep the window from opening automatically?

---

### Post by rbc on 2008-08-04
Alt+F2, then type in gconf-editor. In the box that appears, click:
apps-->nautilus-->preferences, then in the box on the right, uncheck "media auotmount_open. I only have one user on all my machines, so the problem is....I am not sure if this will prevent the drive from opening for all users or just the current one. In other words, the user that plugs the drive in may want it to auto open. Try it and see. If it doesn't do what you want, change it back to the original setting

---

### Post by jon9314 on 2008-08-04
that did the trick. i had to change the setting in all users but it worked thanks.

now is there a way to force any usb media to allow read/write/execute to all local users instead of only the one who plugged it in?

---

### Post by drs305 on 2008-08-04
> **jon9314 said:**
> now is there a way to force any usb media to allow read/write/execute to all local users instead of only the one who plugged it in?

usb devices are not normally meant to be included in fstab because their device name (sdc, sdh) etc has a tendency to change based on what else is currently being used when it is plugged in. 

one method to achieve what you desire would be to use either a uuid or a label to identify them in fstab. then you would mount it with a umask of 000 so that anyone would have read/write/execute capabilities. using umask=000 is not a very secure method. another option would be to create a group and include the users you want, then use the gid to allow them access and alter the umask value accordingly.

Here is an example for a fat32 thumb drive labeled 'usb5':
```
LABEL=usb5  /media/usb500   vfat users,uid=1000,gid=1000,umask=000          0  0
```

---

### Post by jon9314 on 2008-08-09
would there be an error if that thumb drive wasn't plugged in at boot?
i.e. can i still add and remove it like normal while keeping the permissions whenever it is plugged back in.

---

### Post by drs305 on 2008-08-10
jon9314,

It would not create any errors that would display. Fstab would try to mount the device, wouldn't find it, and would move on. When you do mount the device  it should still automount. If not, run "sudo mount -a" and it will mount.

---

