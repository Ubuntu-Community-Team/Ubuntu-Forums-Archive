---
title: "[SOLVED] chown troubles"
date: 2008-07-25
forum: General Help
---

### Post by Tom_ZeCat on 2008-07-25
I'm not sure what I'm doing wrong here.  My goal is to make sure I have ownership of the directory, /home/tom/.kde/share/apps/amarok.  

So that I wouldn't have to type out that long path, I used cd to get to the directory: /home/tom/.kde/share/apps/

I figured the rest would be simple, but I must be doing something wrong.  Here's a cut'n'paste of what I did:

```
tom@toms-jukebox:~/.kde/share/apps$ ls
amarok     d3lphin  juk           kcookiejar  khelpcenter  konsole  RecentDocuments  smb4k
amarokOLD  drkonqi  kconf_update  kfile       konqueror    kwallet  remoteview
tom@toms-jukebox:~/.kde/share/apps$ 
tom@toms-jukebox:~/.kde/share/apps$ pwd
/home/tom/.kde/share/apps
tom@toms-jukebox:~/.kde/share/apps$ sudo chown tom: amarok
sudo: unable to resolve host toms-jukebox
tom@toms-jukebox:~/.kde/share/apps$ sudo chown tom: /amarok
sudo: unable to resolve host toms-jukebox
chown: cannot access `/amarok': No such file or directory
tom@toms-jukebox:~/.kde/share/apps$ sudo chown tom: /amarok/
sudo: unable to resolve host toms-jukebox
chown: cannot access `/amarok/': No such file or directory
```

I wondered if maybe I needed to include the -R parameter since I want ownership of not just the directory, but also of all the files in it and of any subdirectories if they exist.  I tried adding it, but still had problems:  

```
tom@toms-jukebox:~/.kde/share/apps$ sudo chown -R tom: amarok
sudo: unable to resolve host toms-jukebox
tom@toms-jukebox:~/.kde/share/apps$ sudo chown tom: amarok -R
sudo: unable to resolve host toms-jukebox
```

I wondered if the problem is I may need to tell it it's a directory.  Just to see if what I was doing would work on a file, I cd-ed into the amarok directory and tried chown on one of the files in it.  No dice.  Here's what happened:

```
tom@toms-jukebox:~/.kde/share/apps/amarok$ sudo chown -R tom. collection.db
sudo: unable to resolve host toms-jukebox
tom@toms-jukebox:~/.kde/share/apps/amarok$ sudo chown tom. collection.db
sudo: unable to resolve host toms-jukebox
tom@toms-jukebox:~/.kde/share/apps/amarok$ sudo chown tom. collection.db
sudo: unable to resolve host toms-jukebox
tom@toms-jukebox:~/.kde/share/apps/amarok$ sudo chown tom: collection.db
sudo: unable to resolve host toms-jukebox
tom@toms-jukebox:~/.kde/share/apps/amarok$ sudo chown tom :collection.db
sudo: unable to resolve host toms-jukebox
chown: cannot access `:collection.db': No such file or directory

```

As you can see, I've tried changing things up, but haven't had luck yet.  I've googled chown and read over summaries on how to use it, but there must be something that I'm not quite getting.  Any help on this would be greatly appreciated.

---

### Post by sandb on 2008-07-26
Tom,

Seems your problem is not related to chown, but to sudo. I found a [bugreport]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906") on launchpad about this.

The problem would be that your hostname is incorrectly configured somehow.

If after a reboot you still have the same problems i would check the /etc/hosts file contents and see if it contains the following correct names for your loopback ip address:

```
127.0.0.1       localhost
127.0.1.1       toms-jukebox
```

also check the /etc/hostname that has the correct name "toms-jukebox"

If any of these are off, you should try to fix those, reboot and retry.

However, was not able to reproduce your problem on my Gutsy install, so might not be right on the mark...

---

### Post by bhankins on 2008-07-26
Interesting, I didn't have a problem when I tried it your way, but I have never seen an open ended colon used like that in chown.
```
sudo chown tom:tom amarok
```
or just
```
sudo chown tom amarok
```

---

### Post by Tom_ZeCat on 2008-07-27
Many thanks for all the help.  The problem is solved.

---

