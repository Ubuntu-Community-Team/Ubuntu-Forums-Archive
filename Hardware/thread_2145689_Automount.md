---
title: "Automount"
date: 2013-05-16
forum: Hardware
---

### Post by Bigmon on 2013-05-16
Hi, 

Wonder if anyone can help. I have managed to mount a new internal hdd on startup using MountManager, but cannot write to it. Does anyone know if there is an option in MountManager to do this - or is it a bit more complicated than this ?

Cheers !!!!

---

### Post by 2F4U on 2013-05-16
What kind of drives are these, what filesystems? If these are Linux filesystems, who is the owner of the files (userid, group id). If you are not the owner, you can't write. You can, however, try to write with sudo privileges. Are the drives maybe mounted as read-only instead of read/write?

---

### Post by Bigmon on 2013-05-17
Hi, 
This is a  Sata Hard Drive, and the file system according to gparted is ext4 ? I am the administrator, so have sudo privileges. The drop down menu in Mountmanger shows that the drive is read / write. How do I write with "sudo privileges" ?

---

### Post by SlugSlug on 2013-05-17
where is it mounted & is it data only (IE not an OS install)? say its mounted on /mnt/data

```
sudo chown -R yourusername.yourusername /mnt/data
```

---

### Post by Bigmon on 2013-05-18
Sorry, I am not very experienced with this, and do not really understand the question. Is " /media/80gb_HDD" what you are referring too with regards to where it is mounted ? It is an additional internal hard drive and does not contain the operating system.
Cheers.

---

### Post by Bigmon on 2013-05-18
I have just opened the new hard drive again and there is already a folder called "lost+found" there. Not created by myself. If I open this folder I can write to the disk within this folder, but cannot write to the disk outside of this folder.

---

### Post by SlugSlug on 2013-05-18
ok open a terminal and paste

```
sudo chown -R YourUserName /media/80gb_HDD
```

If you dont know YourUserName type 

```
whoami
```

---

### Post by Bigmon on 2013-05-18
Many thanks SlugSlug, that did the trick !

---

