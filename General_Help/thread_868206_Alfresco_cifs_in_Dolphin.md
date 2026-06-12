---
title: "Alfresco cifs in Dolphin"
date: 2008-07-23
forum: General Help
---

### Post by koolguynet on 2008-07-23
I use KDE and dolphin as my file manager (is that the right term?)  Anyway, my company is testing Alfresco to move it into general use by our employees.  They have it working, using CIFS, to access the shares from Windows, but I can't get it to work for my system.  

I type:
smb://servername.com

and I can see the Alfresco file.  After clicking on the file it fails and never asks me for my Alfresco username or password.  Any ideas?

---

### Post by kuja on 2008-07-28
One thing that is worth trying is smbfs. Using it you could mount it like you would any other file system. Worth a try? 

Also, another thing worth trying would be the KDE4  version of Dolphin, which is definitely superior to the KDE3 one.(side note: KDE 4.1 should be out and packaged and probably in the ubuntu 8.04 backports repository before long)

---

### Post by koolguynet on 2008-08-01
I am able to mount the Alfresco share as a Folder using the following:
> 
sudo mount -t cifs //sub.domain.com/Alfresco /home/user/Alfresco/ -o user=user@domain.com

I don't want to always have to mount this drive (or put it in fstab).  I would like to be able to just view it from within Dolphin, like I do with other smb drives.  Any ideas?

---

