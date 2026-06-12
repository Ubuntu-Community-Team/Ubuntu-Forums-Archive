---
title: "Can not share folder"
date: 2008-09-04
forum: General Help
---

### Post by sweet_babylhyn on 2008-09-04
I can shared folder in my my main drive by making some script in smb.conf. My problem is I cant share folder in my other drive that came from other PC. I can't edit the smb.conf of my other drive. It promt me that I have no permission to edit. How can I open my drive thru the password I used in my other PC? Or Is there is a way to reset its password.

Thanks you....

---

### Post by lakersforce on 2008-09-04
*cough*stickies*cough*

---

### Post by aloshbennett on 2008-09-04
Edit /etc/fstab
if you see umask=007 for the drive in question, change it to umask=000
Restart :)

(Basically you are changing the drive permission from 770 to 777 while mounting. Umask is the oppsoite of chmod)

---

### Post by sweet_babylhyn on 2008-09-04
There is no umask in my fstab. See attached file what's inside in fstab.

Thanks in advance

---

