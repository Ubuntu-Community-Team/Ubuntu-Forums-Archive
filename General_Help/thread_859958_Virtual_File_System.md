---
title: "Virtual File System?"
date: 2008-07-15
forum: General Help
---

### Post by rabside on 2008-07-15
hi!
I have a simple question:
on my hdd I have 2 dirs with similar content and I'd like to "mount" them on a unique directory. example:
dir A contains x,y
dir B contains z
dir C shows x,y,z

Is there a way to achieve this?

thx a lot

---

### Post by immolo on 2008-07-15
umm do you mean like the hard drives acting like one?

---

### Post by rabside on 2008-07-15
> **immolo said:**
> umm do you mean like the hard drives acting like one?

exactly, but with dirs

---

### Post by immolo on 2008-07-15
ok so you want one directory say in your home folder and inside it you want to be able to view x,y and z directories there? if it is then I can show you how to do that.

---

### Post by rabside on 2008-07-15
> **immolo said:**
> ok so you want one directory say in your home folder and inside it you want to be able to view x,y and z directories there? if it is then I can show you how to do that.

yes but x,y and z aren't directories but files

---

### Post by fyo on 2008-07-15
Maybe what your are looking for is links?

```
ln -s TARGET LINK_NAME
```

That creates a new file (link) that points to some other file.

---

### Post by immolo on 2008-07-15
ok for files you will have to use ln which is a command to make shortcuts to files use it like this:

```
ln -s /where/ever/Z.file /Where/ever/you/want/to/see/the/file/Z.file
```

That's basically how to use it but with a small amount of trial and error it will work just how you need.

Hope this helps

---

### Post by rabside on 2008-07-15
> **fyo said:**
> Maybe what your are looking for is links?

```
ln -s TARGET LINK_NAME
```

That creates a new file (link) that points to some other file.

if I have handreds of file I can't create a simbolic link for each file

---

### Post by immolo on 2008-07-15
I would link to a directory then myself so have a directory in home with both z and y linked to it then you have access quite easily.

---

### Post by Vivaldi Gloria on 2008-07-15
> **rabside said:**
> if I have handreds of file I can't create a simbolic link for each file

Yes, you can.

Assume you want to symlink the contents of folder1 and folder2 to end_folder.

1) Make sure that non of the folders have files in them with the same names.

2) cd to end_folder and give the command

```
ln -s folder1/* .
```

2) cd to end_folder and give the command

```
ln -s folder2/* .
``` 

That's it.

---

### Post by inteluser on 2008-07-15
In response to your original goal, understand that the situation you describe is a bit tricky - if you were to create a new file in the virtual directory "C", where would it go - in A or B?  It's questions like this that make workarounds like symlinks necessary.

---

### Post by rabside on 2008-07-15
> **inteluser said:**
> In response to your original goal, understand that the situation you describe is a bit tricky - if you were to create a new file in the virtual directory "C", where would it go - in A or B?  It's questions like this that make workarounds like symlinks necessary.

well, the virtual dir C will be read only.

i found this 
[http://www.tagsistant.net/](http://www.tagsistant.net/)

---

### Post by shaggy999 on 2009-07-12
I know this is way old, but what you want to look into 'unionfs'.

---

