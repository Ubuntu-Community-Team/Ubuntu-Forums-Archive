---
title: "Changing Disk Lable/Name, and Permissions"
date: 2010-08-07
forum: Hardware
---

### Post by Rubicon421 on 2010-08-07
I just did a reinstall on my system and now have only one internal HD with just linux on it, and a large NTFS partition for storage. 

When I restart the NTFS partition is not automatically mounted and it is named 945 GB File System. I would like to set it to automount on start up and also would like to rename it. Does anyone know if renaming the drive can mess up any links or other system references to the drive? It shouldn't change the UUID which is what I think everything is going by anyway. 

I really want to fix the automount issue but I only want to rename it if it is completely safe now that other programs are referencing it for music libraries, storage of downloaded files, etc...

---

### Post by Morbius1 on 2010-08-07
Post the output of the following commands so we can see what's up:
```
sudo blkid -c /dev/null
``````
mount
``````
cat /etc/fstab
```

---

### Post by Rubicon421 on 2010-08-07
I got it working with mountmanager. I prefer the GUI approach because I really don't know enough about the terminal and editing config files.

---

