---
title: "help on how to share a directory among different users"
date: 2008-09-16
forum: General Help
---

### Post by news75 on 2008-09-16
hi, I would like share the directory "share" among different users of my unbuntu machine. 
I followed this steps:

#  groupadd share
#  chown -R root.share /home/share
#  chmod 2775 /home/share

now, any user can create a new file in the shared dierctory but the group permission of the new file is only in read. I would like that, any time a user creates a new file, all the users of the group can read and write the new file.
I think I have to change the umask to 007. I tried this solution but any time I close the session the umask value is set to the original value... how to persist the settings I want ?!

thanks 

 news75

---

### Post by iaculallad on 2008-09-16
Instead of 775, make it 777

```
chmod 777 /home/share
```

---

### Post by news75 on 2008-09-16
> **iaculallad said:**
> Instead of 775, make it 777

```
chmod 777 /home/share
```

this will change the directory permissions, but when I will create a new file the new file will have permission according to umask value. so all the files I will create in the directory will have only the read permission for the group...

---

### Post by iaculallad on 2008-09-16
Try setting the sticky bit:

```
sudo chmod -R u+rwX,og-rwx /home/share
```

---

### Post by news75 on 2008-09-16
I set the sticky bit infact every time I create a new file in the share directory the new file belong to the group "share". The problem is that the users of the group "share" have not write rights on the file just created.

---

