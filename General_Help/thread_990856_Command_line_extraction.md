---
title: "Command line extraction"
date: 2008-11-23
forum: General Help
---

### Post by davideotape on 2008-11-23
I just tried to extract a tar.gz using archive manager, but it would not allow me to do this. So, this leads me to believe I will have to sudo the operation in the command line. However, I do not know the code for this. Currently I have the tar.gz in one location, and I want to extract it to another. All help appreciated.

---

### Post by reality1011 on 2008-11-23
tar xvf <file name>

---

### Post by beno1990 on 2008-11-23
If you're getting permission denied errors when you're trying to extract an archive, check both the permission settings of the archive and also the permission settings of the directory you're trying to write the extracted archive to. If the permissions of the directory you're trying to extract to are read only for your user account, it's not going to let you extract there.

---

### Post by neur0 on 2008-11-23
And you need z as in 
tar xvzf <file_name> 
if its a tar.gz (gzipped) archive

---

### Post by reality1011 on 2008-11-23
^ good catch

---

