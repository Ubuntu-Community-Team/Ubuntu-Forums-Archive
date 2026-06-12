---
title: "External HDD in Read only."
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by yarvin on 2006-02-03
I have an external harddrive that I let my cousin use to move files from his old desktop to his new.... he uses windows and when he was done his files were still on the harddrive but the harddrive is in read-only so I can't delete them or add files to the harddrive.... 
how can I fix this in Ubuntu 5.10?

thanks for any help given....

Alvin

---

### Post by frodon on 2006-02-03
If his HDD use NTFS file system (and it should be the case if he use windows) you can't write on it because there is no write support for NTFS under linux because microsoft don't want to give the needed informations.

---

### Post by yarvin on 2006-02-03
soo... I need to format it in windows? :( thats so horrable....

---

### Post by frodon on 2006-02-03
Check first which file system use your hard drive. And then i will tell you which choices you have.

---

### Post by yarvin on 2006-02-03
Ntfs :(

---

### Post by frodon on 2006-02-03
Well, so if you wish to have read/write support under linux you have several ways, i give you a link to a post which explain advantages and disadvantages of each popular FS : [http://www.ubuntuforums.org/showpost.php?p=697500&postcount=4](http://www.ubuntuforums.org/showpost.php?p=697500&postcount=4)

But indeed you will need to format your drive, thanks bill :(

---

### Post by yarvin on 2006-02-03
ok... thanks for the help... :)

---

