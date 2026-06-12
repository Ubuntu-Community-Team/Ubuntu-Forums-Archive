---
title: "what happened to ssh in hardy?"
date: 2008-08-28
forum: General Help
---

### Post by themoo on 2008-08-28
Greetings:
First time poster long time forum snoop. I have a problem using ssh. I have an old laptop that's running Ubuntu 7.X and a new one running Ubuntu 8.X. 
I can SSH just fine with my old laptop. However on the new laptop after I moved all my keys into the .ssh/ directory I was unable to connect to any machines. 
I noticed on 8.0 for some reason ssh keeps creating a id_rsa.keystore file but on my old set up I don't have this file. 
I feel the problem is the new version of SSH that ships with 8.X. Here is the  output of `ssh -V` on each machine.

Old laptop: 
OpenSSH_4.6p1 Debian-5ubuntu0.5, OpenSSL 0.9.8e 23 Feb 2007

New laptop:
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007

I have no idea what to do next. Anyone have any advice?

---

### Post by bodhi.zazen on 2008-08-28
use the -vv flag to get a more verbose output.

I can ssh into ubuntu w/o any problem

```
ssh --vv user@server -i .ssh/<key>
```

where <key> is the key you are using.

---

### Post by mssever on 2008-08-28
Also, verify that the permissions of ~/.ssh and its contents are correct (600 for files and 700 for directories). SSH is very picky about that.

---

### Post by themoo on 2008-08-28
When I run ssh --vv user@server -i .ssh/(my pub key) the command just hangs. On my 7.0 machine however it  just logs me in with ease. 
Also the file/folder permissions are fine. What else can I do?

---

### Post by themoo on 2008-08-29
I also just noticed I can log into my 7.0 machine from my 8.0 machine. But I cannot ssh into computers that are outside of my 192.168.1.x network.

---

### Post by go_beep_yourself on 2008-09-06
What is that id_rsa.keystore created for? I have it from Fedora and wonder if I need it still after installing Ubuntu.

---

