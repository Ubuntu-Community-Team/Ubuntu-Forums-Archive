---
title: "Is there a command for this"
date: 2008-08-28
forum: General Help
---

### Post by dragos240 on 2008-08-28
For deleteing tmp files. My tmp files are clogged.

---

### Post by amitkher on 2008-08-28
What do you mean by tmp files? Files in /tmp?

Are you sure the files you think are tmp files and want to remove are not important files?

---

### Post by dragos240 on 2008-08-28
> **amitkher said:**
> What do you mean by tmp files? Files in /tmp?

Are you sure the files you think are tmp files and want to remove are not important files?
Yes. I cant open any file anymore. I have to save the file now >.>

---

### Post by drs305 on 2008-08-28
The files in /tmp are normally deleted on poweroff. If you turned on the computer today you should probably not delete anything with today's date. On the other hand, if there are files from long ago and you have rebooted since that time they should be safe to delete.

For deleting files from Trash bins, see the link in my signature line. Trash can take up a lot of space which cannot be used until the Trash bins are emptied.

---

### Post by Ryadt on 2008-08-28
Try ```
sudo apt-get autoremove
``````
sudo apt-get clean
```

---

### Post by amitkher on 2008-08-28
> **dragos240 said:**
> Yes. I cant open any file anymore. I have to save the file now >.>

You did not answer the main question. What do you mean by tmp files? Why do you think that they are tmp files and safe to delete?

---

### Post by amitkher on 2008-08-28
> **amitkher said:**
> You did not answer the main question. What do you mean by tmp files? Why do you think that they are tmp files and safe to delete?

EDIT: By "yes", did you answer the first question or the second?

---

### Post by dragos240 on 2008-08-28
> **Ryadt said:**
> Try ```
sudo apt-get autoremove
``````
sudo apt-get clean
```
The autoremove worked great!
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxvidcore4 libx264-57 liblame0 libfaac0
The following packages will be REMOVED:
  libfaac0 liblame0 libx264-57 libxvidcore4
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 1995kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104571 files and directories currently installed.)
Removing libfaac0 ...
Removing liblame0 ...
Removing libx264-57 ...
Removing libxvidcore4 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by dragos240 on 2008-08-28
> **amitkher said:**
> EDIT: By "yes", did you answer the first question or the second?
I ment yes as in i ment the files in /tmp

---

