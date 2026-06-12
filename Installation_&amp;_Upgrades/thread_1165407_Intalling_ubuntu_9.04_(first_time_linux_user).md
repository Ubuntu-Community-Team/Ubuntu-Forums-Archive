---
title: "Intalling ubuntu 9.04 (first time linux user)"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Oveav on 2009-05-20
Well, i booted the cd, and went forward. Then after some text popping up on my monitor I get this message:

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details.

Ubuntu@ubuntu:~$

I tryed searching the forums, and looking trough different installation guides. But Im still clueless what this means. Does it want a password for root, or a username for root? ( I was promised a longer and happier life if I run ubuntu, so I want this to work )

---

### Post by issih on 2009-05-20
I'm guessing you have downloaded the server edition of the cd rom, and consequently you just have the command line interface.

The server edition has no gui by default.
If you want you can try a few commands, e.g. :

```
ls
```
will list all the files in the current directory:

```
ps
```
will list the running processes, etc.

The advice about sudo is telling you that if you want to run a command with root privileges you must prefix the command with sudo.

e.g. "sudo ls" would run ls as root (this is an utterly pointless thing to do, but it illustrates the idea)

I'm assuming you probably wanted a gui so download the desktop edition and give that a whirl instead.

Hope that helps

---

