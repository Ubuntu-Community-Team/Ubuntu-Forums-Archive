---
title: "dell inspiron 3000 as server with ubuntu server"
date: 2014-03-22
forum: Hardware
---

### Post by Ubi_one_2014 on 2014-03-22
hello

in order to replace a NAS for a real pc with a real OS installed on it, i want to buy
a dell inspiron 3000, to be specific, a dell inspiron desktop 3847

i want to install ubuntu server on it, and want to use it as fileserver, backup server, ftp server, cloud backup

is this a good idea?
ubuntu server can be installed on it?
sorry for my non-detailed question, but if i have pitfalls, i look for another brand

---

### Post by TheFu on 2014-03-22
Don't know if that specific model works with Ubuntu. It is unlikely it will not. I run Ubuntu Server on all sorts of Dell machines.

The other things you listed are great ideas - except FTP. Nobody should be running an FTP server anymore. Use sftp instead.

There are many threads here about running file servers. Read a few of those for more ideas. The specific clients involved will determine which file sharing you'll want to use.  sftp works with almost every computer and smartphone platform out there, plus it can be extremely secure if key-based authentication is used - NEVER passwords.

So, if you list the client machines, we can recommend stuff.

---

### Post by Ubi_one_2014 on 2014-03-22
thanks for your answer.

as soon i got the machine, i will report back

---

### Post by TheFu on 2014-03-22
If you are interested in the pre-built NAS software from FreeNAS - it would be smart to review their hardware compatibility "builds" - there are some surprising solutions for $300 or so.  I don't run FreeNAS - it wants too much RAM for my needs, but their hardware builds for storage-centric systems seem smart.

---

