---
title: "can you mount a sftp connection on windows"
date: 2008-09-01
forum: General Help
---

### Post by jerome1232 on 2008-09-01
I currently use my little home server to store important files, I use Winscp as the client on my Vista Laptop.

Is there a way to make a folder on the laptop that either 

a: syncs it's contents via sftp to the server, only transferring files that have changed or have been added.

or

b: make a folder that works like a mounted nfs share would, but going through sftp.

---

### Post by atomkarinca on 2008-09-01
You can mount your ftp folders with [CurlFtpFS]("http://curlftpfs.sourceforge.net/") like this:

```
curlftpfs ftp://username:password@hostname.com/ /home/user/directory
```

---

### Post by jerome1232 on 2008-09-01
hmmm, I'll have to figure out how to compile on windows, I have no idea how to compile programs on windows lol.

---

