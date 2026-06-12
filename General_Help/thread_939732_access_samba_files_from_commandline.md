---
title: "access samba files from commandline"
date: 2008-10-06
forum: General Help
---

### Post by wbloos on 2008-10-06
Hi,

Is it possible to access smb files from bash?
for example i would like to run:
file smb://server/dir/file.ext

I get the "No such file or directory" error.

thx,

WBL

---

### Post by kramulous on 2008-10-06
There could be an easier way, but I'd firstly mount the samba share by:

> sudo mkdir /media/server_dir

sudo mount //server/dir /media/server_dir/ -t cifs -o
user=[sambashare_username],uid=[localmachine username]

Then you can change to /media/server_dir and do whatever.

unmount by:
> sudo umount /media/server_dir

Is this what you were after?

---

### Post by wbloos on 2008-10-06
yes it is!
Had to install smbfs (or the samba package)
```
sudo apt-get install smbfs
```

After that, tyhe mount.cifs manpage is also available, indeed specifying the options you gave me, and more.
```
man mount.cifs
```


thanks!
WBL

---

