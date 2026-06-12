---
title: "Samba unable to create share"
date: 2008-08-13
forum: General Help
---

### Post by CheresZabor on 2008-08-13
Hello, 
i've been having problems with the creation of a share for a second internal hard drive in my machine. 

The error that i get is this:
```
net usershare' returned error 255: net usershare add: cannot share path /media/disk/Share as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.
```
If i only select share and if i select the "allow other people to write to the disk" then the error becomes:
```
Could not change permission of folder
```

if it helps the folder owner is "root" and the hard drive is automounting with settings to default

---

### Post by Ezlo4 on 2008-08-13
I'm not sure exactly what to do but it sounds like you're going to have to log in to root.

---

