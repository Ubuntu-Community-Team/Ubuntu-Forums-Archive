---
title: "Permissions Probble can't write on mounted partition"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by lckl on 2006-07-15
I installed Xubuntu on an ampy hard disk, using the half of the space available. I formatted the remaining space once I Finished the installation, and set it to /home/--user--/storag as a VFAT partition in order to unplug my hard disk later to import the files to windows.

The problem is that i can't write on it. I try mounting it on /media/storage but isn't enables me to write on it. I modified the fstab file already. I set rw, user options but still the same.

I try to chown, ```
sudo chown --user-- /media/storage 
```and the previos location too. ```
sudo chown --user-- /home/--user--/storage
``` but it says operation dennied.

I tried modifying the permissions to 777 but it keeps telling me permission denied.

How can I FIX THIS?

---

