---
title: "World Readable Home Directories?"
date: 2008-07-13
forum: General Help
---

### Post by CarlosinFL on 2008-07-13
I notice a few Linux distributions (Debian / Ubuntu) give every users home directory 755 permissions:

```
drwxr-xr-x 40 carlos carlos 4096 2008-07-12 17:11 carlos

```

I don't understand this logic. In my opinion the only person who should be able to read a users home folder is the owner itself. I can understand if this was a generic share folder located under "/" but I prefer the RPM distributions method of making home directories 700.

Does understand why specific distributions above do this? I don't know if there is a way to change the permissions auto granted to home directories created with the "adduser".

---

### Post by TreeFinger on 2008-07-13
check out /etc/adduser.conf

---

### Post by CarlosinFL on 2008-07-13
> **TreeFinger said:**
> check out /etc/adduser.conf

I am guessing this is what I you are referring to in adduser.conf?

```
# If DIR_MODE is set, directories will be created with the specified
# mode. Otherwise the default mode 0755 will be used.
DIR_MODE=0755

```

---

### Post by jonlemur on 2008-07-13
You can change the permissions with ```
sudo chmod 700 /home/USERNAME
``` just like any other file.  At least it worked for me.  I don't know the rational behind 755 permissions to those folders though.

---

### Post by TreeFinger on 2008-07-13
> **Carlwill said:**
> I am guessing this is what I you are referring to in adduser.conf?

```
# If DIR_MODE is set, directories will be created with the specified
# mode. Otherwise the default mode 0755 will be used.
DIR_MODE=0755

```


Yes, that is what I was referring to. I have never played around with that but you could try. Reading the man page for adduser specifies nothing of this 'DIR_MODE'. There should be a way to do it without changing the adduser.conf but I haven't been able to find anything.

---

