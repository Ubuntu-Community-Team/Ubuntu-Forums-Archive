---
title: "[SOLVED] Problem with Nautilus"
date: 2008-11-03
forum: General Help
---

### Post by katiu on 2008-11-03
Hello everybody!

I have a problem with my personal computer that I can't resolve in any way, even after spending hours on a google search.

I using Nautilus to browse the File System and I noticed that
in a folder where I have photos (jpg format), some items differs between THUMB PREVIEW and OPENED with external tool (example gnome image viewer). Is it a kind of nautilus cache problem  ?

How do I patch it ?

Thanks to all!

Katiuscia

---

### Post by timjohn7 on 2008-11-03
Hi,
Do you mean that some jpgs show as preview and others do not?  This is a setting depending on file size so that large images are not shown in preview.  You can change the size limit in Edit>Preferences>Preview.  if you increase the size, larger files will also show in Preview.

---

### Post by katiu on 2008-11-03
Hello Timjohn7!

I said that I have 2 jpg files that have the same preview, but in reality are 2 different images (if I open this jpg with Gimp I see that are different).

Why have the same preview?

---

### Post by katiu on 2008-11-03
Hello Timjohn7!

I said that I have 2 jpg files that have the same preview, but in reality are 2 different images (if I open this jpg with Gimp I see that are different).

Why have the same preview?

---

### Post by timjohn7 on 2008-11-03
Hi Katiu,
The "preview" icon in Nautilus (for large files, that is files larger than the limit set in Preferences) is just a standard icon, not an actual preview.  If you reduce the size of both images you will see that they have different thumbnails.
Welcome to the forum!

---

### Post by mcallenSchmee on 2008-11-03
Your thumbnails are stored in a folder called .thumbnails in your home folder (the dot in front means it is hidden so you will have to unhide the folder by pressing ctrl-H or going to View> Show Hidden Files). If you delete this folder nautilus will recreate thumbnails for your images which should fix your problem.

---

### Post by katiu on 2008-11-03
Thank you mcallenSchmee!
This solve the problem!

It seems a cach problem with thumb directory .. 

Bye
Katiuscia

---

