---
title: "Un-emptied Trash"
date: 2012-08-05
forum: Hardware
---

### Post by czgirb on 2012-08-05
There is a folder in my Trash. I forgot where the folder come from.
But everytime I tried to press **Empty Trash** or **Delete Permanently**.

An ERROR warning is comeout and said-
> 
** ERROR while deleting**
 There was an error while deleting Beethoven


I tried to:
> * open **Nautilus** > **Edit** > **Preferences** >** Behaviour** Tab > check the **include a Delete command that bypasses trash** > closed
* open **terminal** > type **gksu nautilus** > **Home** folder > **Ctrl+H** > looking for .**Trash** ... but found no .**Trash** there

Please help me ...

---

### Post by ajgreeny on 2012-08-05
Let's see what is in that folder with command ```
ls -l -R .local/share/Trash/files/
```  Maybe one or more of the trash's contents is not owned by you or has a name with a non standard character.

---

### Post by czgirb on 2012-08-06
> **ajgreeny said:**
> Let's see what is in that folder with command ```
ls -l -R .local/share/Trash/files/
```  Maybe one or more of the trash's contents is not owned by you or has a name with a non standard character.

Stranged ... today I found nothing in my Trash

---

### Post by ajgreeny on 2012-08-06
Maybe it is a hidden file in trash.  Try command  ```
ls -al -R .local/share/Trash/files/
```

---

### Post by czgirb on 2012-08-08
> **ajgreeny said:**
> Maybe it is a hidden file in trash.  Try command  ```
ls -al -R .local/share/Trash/files/
```

As requested:
> 
czgirb@czgirb:~$ ls -l -R .local/share/Trash/files/
.local/share/Trash/files/:
total 0
czgirb@czgirb:~$ 


> 
czgirb@czgirb:~$ ls -al -R .local/share/Trash/files/
.local/share/Trash/files/:
total 8
drwx------ 2 czgirb czgirb 4096 Aug  9 00:59 .
drwx------ 5 czgirb czgirb 4096 Jun 27 23:18 ..
czgirb@czgirb:~$ 


SORRY for a late reply ...

---

### Post by drs305 on 2012-08-08
Try this to remove the files:
```
gksu nautilus ~/.local/share/Trash/
```
Highlight the *files* and *info* folders, then use SHIFT-DEL to remove them.
The contents of the folders should be permanently deleted, and the two folders will be recreated when you next delete something.

---

### Post by ajgreeny on 2012-08-08
> **drs305 said:**
> Try this to remove the files:
```
gksu nautilus ~/.local/share/Trash/
```Highlight the *files* and *info* folders, then use SHIFT-DEL to remove them.
The contents of the folders should be permanently deleted, and the two folders will be recreated when you next delete something.
Why **gksu nautilus** for files in the users Trash?  Are you thinking that some of the files my be root owned?

However, I think the OP's **ls -al** output is showing it as empty; it is exactly what I see when my Trash is empty.

---

### Post by drs305 on 2012-08-08
> **ajgreeny said:**
> Why **gksu nautilus** for files in the users Trash?  Are you thinking that some of the files my be root owned?

That would be one explanation of why the OP is having problems with them. The commands show the folders owned by the user, but acting as root should cover all ownership possibilities.

---

