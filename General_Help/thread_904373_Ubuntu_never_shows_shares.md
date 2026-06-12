---
title: "Ubuntu never shows shares"
date: 2008-08-29
forum: General Help
---

### Post by CrusaderAD on 2008-08-29
Why is it when you go Places > Network, Ubuntu never shows the actual file shares on other windows systems? If you go into the system's shortcut, it's always blank.

---

### Post by jigsaws on 2008-08-29
Try to install smbfs first:

sudo apt-get install samba smbfs smbclient

---

### Post by CrusaderAD on 2008-08-29
These are already installed.

---

### Post by fragos on 2008-08-29
Perhaps the shares haven't been mounted. I'm all Linux so I use NFS instead of SAMBA and those shares must be mounted to a folder you've created. The mount would look like this:

sudo mount hostPC.local:/home/user /home/user/folder

dell.local:/home/user is the address of the "host:folder to share" and /home/user/folder is the folder on the client that issued the mount.

---

