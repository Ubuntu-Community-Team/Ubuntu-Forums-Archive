---
title: "CONFUSED with permission for usb HD~~~-_-!"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by piggyaugu on 2005-05-25
confused with the permissions for partitions on usb driver.

i have a usb HD who containing 2 partition, 1 ntfs and 1 FAT32. when connected, I cannot access to the ntfs partition under a normal user but the FAT32 one works. 

I can get into the ntfs partition under root. I've tried to change the permission using *chmod* under root. it doesnt work. Even under X window, the dialog box for changing the permission for this partition is disabled.

I dont know how to manage it. ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Wombley on 2005-05-25
[QUOTE=piggyaugu]confused with the permissions for partitions on usb driver.

i have a usb HD who containing 2 partition, 1 ntfs and 1 FAT32. when connected, I cannot access to the ntfs partition under a normal user but the FAT32 one works. 

I can get into the ntfs partition under root. I've tried to change the permission using *chmod* under root. it doesnt work. Even under X window, the dialog box for changing the permission for this partition is disabled.

I dont know how to manage it. ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]

I *think* the problem here is that the NTFS partition is mounted read-only, therefore you can't change any of the permissions on the files, or modify the files. It is possible to get linux to write to NTFS (the latest knoppix version does it) but I believe the support in ubuntu is a bit sketchy. Try searching the forums for captive-ntfs if you must write to it, I believe it can be done (with some effort). If all you want to do is read the files try [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) .

---

### Post by piggyaugu on 2005-05-26
thx very much.

but that means I cant modify the access permission of a read-only disk??? i mean the permission for the whole partition.

---

### Post by Wombley on 2005-05-26
[QUOTE=piggyaugu]thx very much.

but that means I cant modify the access permission of a read-only disk??? i mean the permission for the whole partition.[/QUOTE]

You can so everyone can read it, just not so that anyone can write it (without doing weird things with captive-ntfs). On the link I gave you I believe it is the "-o umask=0222" part of the mount command which sets the permissions so all users can read it.

---

### Post by migo on 2005-05-26
[QUOTE=Wombley]I *think* the problem here is that the NTFS partition is mounted read-only, therefore you can't change any of the permissions on the files, or modify the files. It is possible to get linux to write to NTFS (the latest knoppix version does it) but I believe the support in ubuntu is a bit sketchy. Try searching the forums for captive-ntfs if you must write to it, I believe it can be done (with some effort). If all you want to do is read the files try [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) .[/QUOTE]

For latest does 3.8.1 still count? I don't have a CD large enough to handle the 3.8.2 ISO.

---

### Post by Wombley on 2005-05-27
[QUOTE=migo]For latest does 3.8.1 still count? I don't have a CD large enough to handle the 3.8.2 ISO.[/QUOTE]

Yes - I think that it's 3.8.0 onwards (looking at the changelog).

---

### Post by jobezone on 2005-05-27
[QUOTE=piggyaugu]confused with the permissions for partitions on usb driver.

i have a usb HD who containing 2 partition, 1 ntfs and 1 FAT32. when connected, I cannot access to the ntfs partition under a normal user but the FAT32 one works. 

I can get into the ntfs partition under root. I've tried to change the permission using *chmod* under root. it doesnt work. Even under X window, the dialog box for changing the permission for this partition is disabled.

I dont know how to manage it. ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]
 ```
/dev/hda1       /mnt/winNTFS    ntfs    noauto,users,exec,utf8,umask=000        0       0
```

This is the line I have in /etc/fstab pointing to my NTFS partition. I think it's either "users" or "umask=000" you'll need to add to be able to read it as a user.

---

