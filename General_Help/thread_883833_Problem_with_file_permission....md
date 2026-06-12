---
title: "Problem with file permission..."
date: 2008-08-08
forum: General Help
---

### Post by spotdog14 on 2008-08-08
Hello, I seem to be running into a problem with file permission. Here is my situation, I got a new laptop and was copying over various files from my old /home partition from my old laptop to my new one. But when I go to move them it says that I do not have permission, now when I go to the permissions tab it says that "nobody" owns the folder. 

How do I change this so that I can take over ownership of these folders?

Thanks.

---

### Post by x1a4 on 2008-08-08
Hi,

```
sudo chown -R *user*:*group* /home/user
```
Where *user*:*group* is the user name and group name the ownership of the directory will be set to.  The -R option will change ownership recursivelly.

---

### Post by PmDematagoda on 2008-08-08
The following command(for directories):-
```
sudo chmod -R 777 name-of-directories
```
or(for files):-
```
sudo chmod -R 777 name-of-file
```
should do it. But please be careful where you execute those commands.

---

### Post by Sycron on 2008-08-08
You can try with
```
sudo chown -R your-name-here /your/full/path/here/*
```and then umount/mount partition ...

---

### Post by silkstone on 2008-08-08
That may be because you have a different username on your new machine, or because things got messed up by the transfer.

Change ownership by...

sudo chown -R yourusername:yourusername /path/to/folder

You may also need to change permissions with the chmod command, but see if the above solves it first.

@ Sycron - You don't need the * on the end - the -R is recursive and changes the ownership of everything. ;)

---

### Post by spotdog14 on 2008-08-08
> **PmDematagoda said:**
> The following command(for directories):-
```
sudo chmod -R 777 name-of-directories
```
or(for files):-
```
sudo chmod -R 777 name-of-file
```
should do it. But please be careful where you execute those commands.



Awesome, thank you very much! I used the:

```

sudo chmod -R 777 directory name

```

It worked great. On a side note why does Pidgin use .purple for its settings instead of something like .pidgin?

---

