---
title: "Tweaking Terminal Move Command"
date: 2008-07-31
forum: General Help
---

### Post by sandman3838 on 2008-07-31
Hello

This should be a simple one for you guys and gals!

As an example lets say I want to move a "folder" FOLDER_A from my desktop to, /home/USERNAME/.icons

ANS - TERMINAL:
sudo mv ~/Desktop/FOLDER_A /home/USERNAME/.icons

QUESTION (Issue!):
What would I type if I wanted to leave the folder on the desktop but Move all the files in that folder to another another folder?
TARGET FOLDER:
/Desktop/FOLDER_A

DESTINATION FOLDER:
/home/USERNAME/.icons

I have seen several list on the base commands and I have even made a spreadsheet but to keep track of them but I can't seem to find anything on this?

Thank you all for you help!:)

---

### Post by sisco311 on 2008-07-31
```
mv  ~/Desktop/FOLDER_A/* ~/.icons/
```~ = /home/[I]username
[/I]*  = all the files and folders

---

### Post by sandman3838 on 2008-07-31
Thank you!
Thank you!
That's what I was looking for!:)

---

### Post by mali2297 on 2008-07-31
Also, don't use sudo when managing your own files; the ownership might then change to root.

---

### Post by sisco311 on 2008-07-31
> **mali2297 said:**
> Also, don't use sudo when managing your own files;
i agree, sudo is unnecessary in this case.
> **mali2297 said:**
> the ownership might then change to root.
just curious, can you give us an example?

---

### Post by mali2297 on 2008-07-31
> **sisco311 said:**
> i agree, sudo is unnecessary in this case.

just curious, can you give us an example?

After some research, it seems that *mv* is not that sensitive to this. But say, if you unpack a downloaded theme with *sudo tar*, then root will be the owner of the extracted files.

---

### Post by sisco311 on 2008-07-31
> **mali2297 said:**
> After some research, it seems that *mv* is not that sensitive to this. But say, if you unpack a downloaded theme with *sudo tar*, then root will be the owner of the extracted files.
nope
> *sisco*@*acme*:/root$ sudo tar -xvvzf /home/*sisco*/test/2.tar.gz 
drwxr-xr-x *sisco/sisco*       0 2008-08-01 01:35 2/
-rw-r--r-- *sisco/sisco *     33 2008-08-01 01:34 2/1

* sisco@acme*:/root$ ls -al
total 18
drwxr-xr-x 13 root  root  1024 2008-08-01 01:44 .
drwxr-xr-x 22 root  root  1024 2008-07-03 21:25 ..
drwxr-xr-x  2 root  root  1024 2008-07-14 12:44 1
drwxr-xr-x  2 *sisco sisco* 1024 2008-08-01 01:35 2


---

### Post by jerome1232 on 2008-07-31
```
jeremy@ubuntu:~/backup/test$ ls -l
total 16
-rw-r--r-- 1 jeremy jeremy  1555 2008-07-31 15:52 stuff
-rw-r--r-- 1 jeremy jeremy 10240 2008-07-31 15:52 stuff.tar
jeremy@ubuntu:~/backup/test$ sudo mv stuff stuff1
Password:
jeremy@ubuntu:~/backup/test$ ls -l
total 16
-rw-r--r-- 1 jeremy jeremy  1555 2008-07-31 15:52 stuff1
-rw-r--r-- 1 jeremy jeremy 10240 2008-07-31 15:52 stuff.tar
jeremy@ubuntu:~/backup/test$ sudo cp stuff1 stuff
jeremy@ubuntu:~/backup/test$ ls -l
total 20
-rw-r--r-- 1 root   root    1555 2008-07-31 15:53 stuff
-rw-r--r-- 1 jeremy jeremy  1555 2008-07-31 15:52 stuff1
-rw-r--r-- 1 jeremy jeremy 10240 2008-07-31 15:52 stuff.tar
```

that's cool I didn't know mv preserved permissions (does it only do that when run as root, like tar?)

I think he was referring to what happens when you use cp

---

### Post by mali2297 on 2008-07-31
> **sisco311 said:**
> nope

Did you create the archive yourself? If the archived files were owned by you, then tar remembers it.

I mean if you download an archive from the internet and the original owner is not known to the system.

---

### Post by mali2297 on 2008-07-31
> **jerome1232 said:**
> ```
jeremy@ubuntu:~/backup/test$ ls -l
total 16
-rw-r--r-- 1 jeremy jeremy  1555 2008-07-31 15:52 stuff
-rw-r--r-- 1 jeremy jeremy 10240 2008-07-31 15:52 stuff.tar
jeremy@ubuntu:~/backup/test$ sudo mv stuff stuff1
Password:
jeremy@ubuntu:~/backup/test$ ls -l
total 16
-rw-r--r-- 1 jeremy jeremy  1555 2008-07-31 15:52 stuff1
-rw-r--r-- 1 jeremy jeremy 10240 2008-07-31 15:52 stuff.tar
jeremy@ubuntu:~/backup/test$ sudo cp stuff1 stuff
jeremy@ubuntu:~/backup/test$ ls -l
total 20
-rw-r--r-- 1 root   root    1555 2008-07-31 15:53 stuff
-rw-r--r-- 1 jeremy jeremy  1555 2008-07-31 15:52 stuff1
-rw-r--r-- 1 jeremy jeremy 10240 2008-07-31 15:52 stuff.tar
```

that's cool I didn't know mv preserved permissions (does it only do that when run as root, like tar?)

I think he was referring to what happens when you use cp

Yes, that was what I had in mind, but I did the test wrong.
```

[~]$ touch hello world
[~]$ ls -l hello world
-rw-r--r-- 1 mali2297 mali2297 0 2008-08-01 01:09 hello
-rw-r--r-- 1 mali2297 mali2297 0 2008-08-01 01:09 world
[~]$ sudo cp hello world
[~]$ ls -l hello world
-rw-r--r-- 1 mali2297 mali2297 0 2008-08-01 01:09 hello
-rw-r--r-- 1 mali2297 mali2297 0 2008-08-01 01:10 world
[~]$ rm world
rm: remove regular empty file `world'? y
removed `world'
[~]$ sudo cp hello world
[~]$ ls -l hello world
-rw-r--r-- 1 mali2297 mali2297 0 2008-08-01 01:09 hello
-rw-r--r-- 1 root     root     0 2008-08-01 01:10 world

```
Apparently, if the file you copy to already exists, the ownership won't change.

---

### Post by sisco311 on 2008-07-31
thanks

---

