---
title: "help with scp"
date: 2008-10-12
forum: General Help
---

### Post by a_weasel on 2008-10-12
I cant figure out how to use scp.

I'm logged in to a remote host in this example.
```
cory [8] ~/projdump/proj1 > ls
build/                    manifest.mf               src/
draw.java                 PUBLIC-VERSION
Makefile                  README-AND-DONT-TURN-IN
cory [9] ~/projdump/proj1 > scp draw.java daren@daren-laptop:~/Documents
ssh: daren-laptop: node name or service name not known
lost connection
cory [10] ~/projdump/proj1 > 

```

Apparently "daren-laptop" is the wrong thing to put, but I don't know what else to put. Just as an example, this is what my terminal says on my computer:

```
daren@daren-laptop:~$ ls
Desktop    Examples  NetBeansProjects  Public      Templates
Documents  Music     Pictures          RandomShit  Videos
daren@daren-laptop:~$ 

```

thanks for any help.

---

### Post by Sam on 2008-10-12
If you don't have a SSH server on your pc you must use scp FROM your pc TO the host (and not while you're connected to the host).

Example:
```
daren@daren-laptop:~$ scp user@host:~/projdump/proj1/draw.java .
```
To copy the file to the current folder.

If it's to copy in the other way:
```
daren@daren-laptop:~$ scp myfile user@host:~/someplace
```

---

### Post by a_weasel on 2008-10-12
beautiful. thank you.

---

### Post by Sam on 2008-10-12
Oh, I forgot to say that you can use SSH in nautilus. Just type in location bar: **ssh://user@host**
It could be easier for files manipulation.

---

### Post by a_weasel on 2008-10-13
oh man. i give that way an A+ high-five. nice. thanks.

---

### Post by paris_alex on 2008-10-13
if you want to access remote files as a local directory, check out sshfs. it allows you to mount any directory from an ssh connection. it rocks!

---

