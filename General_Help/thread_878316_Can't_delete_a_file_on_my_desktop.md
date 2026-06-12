---
title: "Can't delete a file on my desktop"
date: 2008-08-02
forum: General Help
---

### Post by 522viper on 2008-08-02
It states,
Cannot move file to trash, do you want to delete immediately?
The file "Crack" cannot be moved to the trash.

Unable to trash file: Permission denied

then I try to delete it and it gives me..
Error while deleting+

This file came off a cd and I want to delete it. I cant delete it let alone move it.

Any ideas?

Edit: I deleted it using sudo.

---

### Post by sisco311 on 2008-08-02
run the following command from a terminal:
(Applications -> Accessories -> Terminal)
```
sudo chown -R $USERNAME: ~/Desktop
```then try to delete the file.

---

### Post by Tom_ZeCat on 2008-08-02
He's right.  Since you took the file from a CD, you don't own it.  Linux is set up so that you must own any files you delete so that, on a network, people don't go around deleting other people's files.  

By using the chown command as shown in the post above, you'll take ownership and then be able to delete the file.

---

