---
title: "Need to delete many folders and files"
date: 2008-11-25
forum: General Help
---

### Post by alan_uk on 2008-11-25
I have just transferred to my desktop a data dvd containing hundreds of files and folders as a temporary measure. I now need to delete them but can't because of the padlock icon.  I can do them in batches by going into Properties and then permissions but this is going to take far too long. Is there a way of unsecuring these files wholesale?

---

### Post by linux_tech on 2008-11-25
Try
chmod a+x /media/nameofdvd
or path to dvd

---

### Post by alan_uk on 2008-11-25
Thanks but I no longer have the dvd

---

### Post by ubun_two on 2008-11-25
You could try:

sudo chown -R yourid:yourgroup /yourdatalocation
sudo chmod -R 644 /yourdatalocation

This should change the owner and the permission of the content of your directory recursively, so that you can do whatever you need to the data.

---

### Post by gettinoriginal on 2008-11-25
I just do Alt > F2 and enter gksu nautilus and it allows me root access to all the files.  Just be careful what you delete while in it.

---

### Post by alan_uk on 2008-11-25
Hey thanks that did it! Had me worried for a while. Thought I would have to do a total reinstall and build - thanks again

---

