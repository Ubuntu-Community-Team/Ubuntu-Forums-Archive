---
title: "Setting default 666 permission to new files in a shared NFS folder?"
date: 2005-11-20
forum: General Help
---

### Post by BathroomNinja on 2005-11-20
OK, so I have a desktop and a laptop for my wife.  Both running Breezy, latest everything.  I got NFS running and working on both thanks to the wiki.ubuntu howto.  Here is what I'm trying to do for my wife.

On both the desktop and the laptop, she has a 'Documents' folder under /home/wendy
So, '/home/wendy/Documents'

The 'real' folder exsists on the desktop and is shared with NFS to the laptop.  so the laptop mounts desktop:/home/wendy/Documents  to the local /home/wendy/Documents on boot.

Works great, EXCEPT...  When she creates a document on the laptop and saves it to the folder (or visa versa), the other computer can not modify the file, only read it since the permissions default to allowing only the person who created the file to edit the file.  So she complains, and I have to manually chmod the files to 666 to allow her to edit them on her desktop or visa versa.

I'm sure I could run a script that chmod's every file in that directory to 666 every minute or so, but that seems like a shoddy way to do it.  Is there a way to have it default to 666?  I'd kinda like to be able to use MY desktop to access files and edit them as well.


On the desktop, I have the following in /etc/exports  
```
/home/wendy/Documents 192.168.2.11(rw,async)
```
Where 192.168.2.11 is the laptop

That's the only thing I can think of that I might be able to change to be able to do this by default.  I have searched around and around and came up empty so now, I plead to the forums.

---

### Post by BathroomNinja on 2005-11-20
ok, so I added no_root_squash to the server's /etc/exports
Also, I added rw to the mount options on the laptop.

Same thing.  But then again, all that's supposed to do is allow read and write of the folder, and I already had that.

---

### Post by BathroomNinja on 2005-11-22
Anyone?  Bueler?  Bueler?  Anyone?

---

### Post by nyktovus on 2007-12-08
having a similar issue.. does SOMEONE out there understand nfs?

Nykto.

---

