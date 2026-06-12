---
title: "behaviour of rm in interpid"
date: 2008-11-01
forum: General Help
---

### Post by Azrael-ru on 2008-11-01
What is it? Is this some type of user-friendly stuff?
I'm confused:

```
root@localhost# touch /home/azrael/file
azrael@localhost:~$ ls -l file
-rw-r--r-- 1 root root 0 2008-11-02 05:16 file
# here start magic
azrael@localhost:~$ rm file
rm: delete write-protected file `file'? y
azrael@localhost:~$ ls -l file
ls: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087; &#1082; file: No such file or directory
```

that's it. root's file deleted by unpriviliged user.

of course it shorter, than 'sudo rm',
but i was shocked by that unexpected operation.
Can i disable it, at same time keep sudo functionality?
I guess this operation allow for 'admin' group, am i right?
This is new feature or i just discover it too late?

```
azrael@localhost:~$ cat /etc/group | grep azrael
adm:x:4:azrael
dialout:x:20:azrael
cdrom:x:24:azrael
floppy:x:25:azrael
audio:x:29:azrael
dip:x:30:azrael
video:x:44:azrael,vdr
plugdev:x:46:azrael
syslog:x:103:azrael
fuse:x:107:azrael
lpadmin:x:109:azrael
admin:x:114:azrael
azrael:x:1000:www-data
sambashare:x:123:azrael
```

fileutils installes from repository, no 3rd-party

```
azrael@localhost:~$ rm --version
rm (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
```

Thank you.

---

### Post by dcstar on 2008-11-01
> **Azrael-ru said:**
> What is it? Is this some type of user-friendly stuff?
I'm confused:

```
root@localhost# touch /home/azrael/file
azrael@localhost:~$ ls -l file
-rw-r--r-- 1 root root 0 2008-11-02 05:16 file
# here start magic
azrael@localhost:~$ rm file
rm: delete write-protected file `file'? y
azrael@localhost:~$ ls -l file
ls: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087; &#1082; file: No such file or directory
```

that's it. root's file deleted by unpriviliged user.
.......

If you used the user that you installed the system with, then that is **not** an "unprivileged" user, it is a user with high privileges just under root status.

---

### Post by russlar on 2008-11-01
Well, this is most unusual...

```
russlar@knomad:~$ cd tmp/rmtest/
russlar@knomad:~/tmp/rmtest$ ls -l
total 0
-rw-r--r-- 1 root root 0 2008-11-01 21:44 file
russlar@knomad:~/tmp/rmtest$ rm file
rm: remove write-protected regular empty file `file'? y
russlar@knomad:~/tmp/rmtest$ ls -alrth
total 8.0K
drwxr-xr-x 5 russlar russlar 4.0K 2008-11-01 21:43 ..
drwxr-xr-x 2 russlar russlar 4.0K 2008-11-01 21:45 .
russlar@knomad:~/tmp/rmtest$

```

and could be a security hole. Bug???

---

### Post by russlar on 2008-11-01
> **dcstar said:**
> If you used the user that you installed the system with, then that is **not** an "unprivileged" user, it is a user with high privileges just under root status.

that can delete root-owned files without the -f flag?

---

### Post by ju2wheels on 2008-11-01
When you type in sudo for any command it stays active for a few minutes after, this is why it doesnt ask you for your password each and every time you use sudo. Is it possible you still had the sudo permission active when you ran rm?

---

### Post by russlar on 2008-11-01
> **ju2wheels said:**
> When you type in sudo for any command it stays active for a few minutes after, this is why it doesnt ask you for your password each and every time you use sudo. Is it possible you still had the sudo permission active when you ran rm?

nope- brand new shell session.

besides, sudo rights only get used when sudo is invoked in the command.

---

### Post by Azrael-ru on 2008-11-01
> **dcstar said:**
> If you used the user that you installed the system with, then that is **not** an "unprivileged" user, it is a user with high privileges just under root status.

ok, i get it. thanks.
this new in intrepid or already been?

---

### Post by dcstar on 2008-11-01
> **Azrael-ru said:**
> ok, i get it. thanks.
this new in intrepid or already been?

Not 100% sure, but I think it's been there for a while.

---

### Post by Azrael-ru on 2008-11-01
> **russlar said:**
> and could be a security hole. Bug???

Well, i don't want talk about this as security hole, after all, you still can 'sudo rm'

---

### Post by russlar on 2008-11-01
> **Azrael-ru said:**
> ok, i get it. thanks.
this new in intrepid or already been?

This (install user being administrator) is not new. The behavior we've seen (that user deleting root's files) is not.

---

### Post by ju2wheels on 2008-11-01
> **russlar said:**
> nope- brand new shell session.

besides, sudo rights only get used when sudo is invoked in the command.

I know that but just wanted to double check it wasnt an unwanted side effect (as in rm was being granted that privilege just because you ran sudo prior to using it), but from your statement that isnt the case.

---

### Post by ad_267 on 2008-11-01
Wow that is weird, it happens here too. And the sudo isn't remaining on, because I opened up a new terminal and it still worked.

I think this only happens if the file is in the users home directory. I tried this in my home directory and I could delete a file owned by root, but I couldn't remove a file from outside my home directory without sudo.

I would still consider this a bug.

---

### Post by Azrael-ru on 2008-11-01
more and more.. ))
now without confirm at all

```

azrael@localhost:~$ ls -l file
-rw-r--r-- 1 root root 0 2008-11-02 07:07 file
azrael@localhost:~$ mv file file2
azrael@localhost:~$ ls -l file2
-rw-r--r-- 1 root root 0 2008-11-02 07:07 file2
azrael@localhost:~$


```

---

### Post by wgrant on 2008-11-01
All that matters for removing files is write access to the parent directory! This perfectly normal behaviour.

---

### Post by ad_267 on 2008-11-01
Edit. Never mind, wgrant is right.

---

### Post by Azrael-ru on 2008-11-02
> **wgrant said:**
> All that matters for removing files is write access to the parent directory! This perfectly normal behaviour.

It quite logic, but what if i want place file in user directory with write-protection and i want that exactly this file can't be removed, at same time i want that user still have control to user-owned files.
(if just '$: chmod a-w ~' user can't create/remove files, am i right?)

So, can i do something with this?

Thanks.

---

### Post by russlar on 2008-11-02
> **wgrant said:**
> All that matters for removing files is write access to the parent directory! This perfectly normal behaviour.

Ok, so as long as root owns /etc/ or /usr/, a normal user would not be able to move/delete files in those dirs.

---

