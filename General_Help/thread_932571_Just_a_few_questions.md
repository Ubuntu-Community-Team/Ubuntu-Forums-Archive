---
title: "Just a few questions"
date: 2008-09-28
forum: General Help
---

### Post by sxen on 2008-09-28
Hey,

I just had a few questions and wasn't sure where to post them, I hope this is the right place.

1) If you have a terminal open under a folder say
 "user@linux:/home/user/Desktop" or whatever is it then possible to type in a command that will open that folder in a window using the GUI? Hope that made sense. >.<

2) How do you change folder permissions via a terminal? I don't want to log into the root user or anything like that. =P

3) How do I change the permissions of an individual file via the terminal?

Errm, I forgot my other questions as I was typing. Never mind. I could probably find an answer to question two but I though I would ask while I was here. 

Thanks

---

### Post by kokkus on 2008-09-28
Yes, write nautilus.
To get promission access you can type gksudo nautilus, right-click, properties, promission.

If this is what you ment.

---

### Post by jespdj on 2008-09-28
You use the **chmod** command in a terminal to change permissions for files or folders. For example, to make a file or folder read-only, type:
```
chmod a-w filename
```
The "a" stands for "all" and "-w" for removing the "writable" permission. Type "man chmod" for a complete description of how chmod works.

---

### Post by Elfy on 2008-09-28
You can open nautilus anywhere 

```
nautilus ~/Desktop/folder
nautilus /etc
```

If you opened it without root rights in the system - you can read but not write.

---

