---
title: "Can't edit HD"
date: 2008-10-08
forum: General Help
---

### Post by kaelonlloyd on 2008-10-08
i've found out how to mount my Hardrive, but it is Read only.

i used this code:
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

any help

---

### Post by mikewhatever on 2008-10-08
To check if you are the owner, run <ls -l /media>.

Thank you vanadium, I've got umask confused with chmod.

---

### Post by vanadium on 2008-10-08
I don't agree with that advice. For read/write and execute access, the umask bit should be 0.

However, what is really preventing you from writing to this disk is the driver you use. You should change "ntfs" by "ntfs-3g". Then set umask to "0000" to allow anyone to use the disk.

---

