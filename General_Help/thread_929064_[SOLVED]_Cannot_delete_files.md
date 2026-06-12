---
title: "[SOLVED] Cannot delete files"
date: 2008-09-24
forum: General Help
---

### Post by init1 on 2008-09-24
This is really weird. I have some file on my hard drive that I cannot delete, even though I have used chmod 777 on them. ls -l confirms this. Every time I try, I get 
```

rm: cannot remove `*filename*': Permission denied

```
They can only be removed with root. What's going on?!
Edit: chmod was also used and had no effect

---

### Post by drs305 on 2008-09-24
chmod can change the read, write and execute permissions of a file but doesn't change the owner. For that, you would have to use the *chown* command (coupled with 'sudo') to change ownership before you could delete it as a normal user.

Alternately, you could open nautilus or another file browser with "gksu nautilus" to have root permissions via the browser to delete files (but be careful). Another option is to combine "sudo" with the "rm" command, but now you are definitely flirting with trouble if you make a mistake.

---

### Post by init1 on 2008-09-24
> **drs305 said:**
> chmod can change the read, write and execute permissions of a file but doesn't change the owner. For that, you would have to use the *chown* command (coupled with 'sudo') to change ownership before you could delete it as a normal user.

Alternately, you could open nautilus or another file browser with "gksu nautilus" to have root permissions via the browser to delete files (but be careful). Another option is to combine "sudo" with the "rm" command, but now you are definitely flirting with trouble if you make a mistake.
Yeah, I used chmod on it too. Here's the what ls -l gives me:
```

-rwxrwxrwx 1 user user    576 2008-09-24 16:41 f1_help.txt

```
Edit:
I know that I use can root to delete them, but I shouldn't have too.

---

### Post by porchrat on 2008-09-24
> **init1 said:**
> Yeah, I used chmod on it too. Here's the what ls -l gives me:
```

-rwxrwxrwx 1 user user    576 2008-09-24 16:41 f1_help.txt

```
Edit:
I know that I use can root to delete them, but I shouldn't have too.

Is that "user" in the file info the same user that is trying to delete the file?  Or does the user that is trying to delete the file belong to that "user" group?

If not you can do this:
```
sudo chown new_user:new_user f1_help.txt
```

---

### Post by init1 on 2008-09-24
> **porchrat said:**
> Is that "user" in the file info the same user that is trying to delete the file?  Or does the user that is trying to delete the file belong to that "user" group?

If not you can do this:
```
sudo chown new_user:new_user f1_help.txt
```
Yes, that user owns it, or appears to own it. 
Ok, this is really weird. I can edit it, but I can't delete it. Like I can do:
```

$echo weird >*filethatwontdelete*
$cat *filethatwontdelete*
weird
$

```
Does this help any, or is this just a really strange bug?

---

### Post by drs305 on 2008-09-24
Unless you are "*user", *I don't think you are understanding what we are saying. You used chmod with root privileges to change read, write and execute permissions. Thus, you can *edit* the file. But you DO NOT own the file, and only root and the owner can delete it. 

chmod will not change that. Only the ***owner*** or root can delete the file.

Here is the ubuntu wiki on permissions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by init1 on 2008-09-24
> **drs305 said:**
> Unless you are "*user", *I don't think you are understanding what we are saying. You used chmod with root privileges to change read, write and execute permissions. Thus, you can *edit* the file. But you DO NOT own the file, and only root and the owner can delete it. 

chmod will not change that. Only the ***owner*** or root can delete the file.

Here is the ubuntu wiki on permissions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")
Yes, I use "user" as my user name. Thus, I should be the owner.

---

### Post by drs305 on 2008-09-24
> **init1 said:**
> Yes, I use "user" as my user name. Thus, I should be the owner.

Then it is I that didn't understand what *you* were saying. My guess is that ubuntu is getting confused with a username of "user".  ;-)

---

### Post by Iowan on 2008-09-24
I'm probably barking up wrong tree - again...
Check the directory in which the file is located - "user" may need rights there, too.

---

### Post by init1 on 2008-09-24
> **Iowan said:**
> I'm probably barking up wrong tree - again...
Check the directory in which the file is located - "user" may need rights there, too.
Yep, that worked. I didn't realize that a file that you own can't be removed from a folder that you don't, but it makes sense. Thanks!
Thanks also to everyone else who responded, I appreciate it :D

---

### Post by porchrat on 2008-09-25
mark as solved please...so that others may benefit from the guru wisdom...

Seacrest out!

---

