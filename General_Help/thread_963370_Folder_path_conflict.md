---
title: "Folder path conflict"
date: 2008-10-30
forum: General Help
---

### Post by aliov_85 on 2008-10-30
Hello

I've mounted a windows share on my desktop 

> mount -t smbfs -o username=xxx,password=xxxx //xxxx.xxxx.xxxx.xxxx/paso/backup/termograf home/smuz/Desktop

I put this command in "rc.local" in order to mount the windows share. 

But now everything from windows share is copied to my desktop and I erased the command that is executed at startup and I still have problems.

The problem is that every thing that /home/smuz folder is copied to the Desktop and if I remove a folder from Desktop, it's also deleted from  /home/smuz.

Also if I create a folder in Desktop, it's also created in /home/smuz


I appreciate very much any help it's very urgent

---

### Post by quibbler on 2008-10-30
If you haven't install Configuration Editor.
In synaptic it is called gconf-editor.
Start the editor (you find it under System Tools) and 
go to apps - nautilus - pereferences  and make sure that
desktop_is_home_dir is NOT checked.

Regards quibbler

---

### Post by aliov_85 on 2008-10-30
Thank you Quibber.

I verfied and in fact it was not checked.

So what should I do?

Regards

---

