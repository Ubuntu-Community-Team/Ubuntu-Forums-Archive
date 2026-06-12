---
title: "Permission Problems"
date: 2008-10-17
forum: General Help
---

### Post by G-Dub on 2008-10-17
Hello, I am having difficulties copying files from DVD I burned on a windows machine. It's say I don't have permission. So I tried opening the root file manager by using this code:
```
kdesudo konqueror
```
This opened up konqueror in Root but it doesn't see and media attached and there is nothing in my home folder! How am i supposed to change the permission on this DVD?
I Tried ```
sudo chown -R $garrett:$garrett /media/cdrom0
```
That failed... i tried going into- Kmenu -> System Settings -> User Management -> Modify -> and Change the Privileges and Groups to allow me to access root...

No matter what I do it says I Cannot change permissions on cdrom0.

---

### Post by RealPSL on 2008-10-18
The CDROM/DVDROM is read-only media. Changing permissions on any device requires write permissions.

---

### Post by Yellow Pasque on 2008-10-18
Try adding your user to the cdrom group if you're not in it already.
```
gksudo gedit /etc/group
```

> This opened up konqueror in Root but .. there is nothing in my home folder!
If you opened konqueror as root, it will show /root as your home folder

---

