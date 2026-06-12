---
title: "A few command line questions"
date: 2008-07-17
forum: General Help
---

### Post by z.s.tar.gz on 2008-07-17
I have 2 Questions:

1. How do you change file and folder permisions in terminal.
(I need to make a folder and all sub files/folders read-only)

2. How can I copy all files in a folder without copying the actual folder, and still keep subdirectories intact?

Please Help

---

### Post by dracayr on 2008-07-17
1. chmod is the command, use the octal code

2. cp foldername/* destinationfolder/

dracayr

---

### Post by Pettman on 2008-07-17
> **z.s.tar.gz said:**
> I have 2 Questions:

1. How do you change file and folder permisions in terminal.
(I need to make a folder and all sub files/folders read-only)
Use the program chmod, for exact syntax see **man chmod**. Here's a good page about it [http://www.zzee.com/solutions/chmod-syntax.shtml](http://www.zzee.com/solutions/chmod-syntax.shtml)
> **z.s.tar.gz said:**
> 2. How can I copy all files in a folder without copying the actual folder, and still keep subdirectories intact?

Please Help
I'd try **cp -r the_folder/* target**
To find out what a command does, use **man command**

---

### Post by DGortze380 on 2008-07-17
> **z.s.tar.gz said:**
> I have 2 Questions:

1. How do you change file and folder permisions in terminal.
(I need to make a folder and all sub files/folders read-only)

2. How can I copy all files in a folder without copying the actual folder, and still keep subdirectories intact?

Please Help


dracayr's post is correct, but to clarify. To make the folder/file **read-only** for all users (owner,group,other).

```

chmod 444 /path/to/file/or/folder

```

read only for owner and group, no access for other would be 440
check this page out for more info: [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by dracayr on 2008-07-17
If you want to copy a folder and keep file permissions, you have to use 
cp -a

dracayr

---

### Post by z.s.tar.gz on 2008-07-17
Thanks! That answers all my questions!
I love the ubuntu world.

---

### Post by z.s.tar.gz on 2008-07-17
Oops.
I just thought of another thing:

How can I apply the same permissions to the same sub-everything.

---

### Post by dracayr on 2008-07-17
```
chmod -r
```

always check the manpages, they're a reliable source of information:

```
man chmod
```

dracayr

---

### Post by z.s.tar.gz on 2008-07-17
I mean, I try and do chmod -r 644 /directory

but it says something like "unknown directory '644'"
Am I using the wrong syntax?

---

### Post by Vivaldi Gloria on 2008-07-17
> **z.s.tar.gz said:**
> I mean, I try and do chmod -r 644 /directory

but it says something like "unknown directory '644'"
Am I using the wrong syntax?

It is "-R" not "-r".

---

### Post by z.s.tar.gz on 2008-07-17
Oh. Ok.

Thank you so much! I love ubuntu!

---

