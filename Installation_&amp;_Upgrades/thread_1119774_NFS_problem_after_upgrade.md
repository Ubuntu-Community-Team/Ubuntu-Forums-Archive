---
title: "NFS problem after upgrade"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by zhushazang on 2009-04-08
Hey.

I have a small cluster with some scientific apps (gaussian, crystal,
etc). The version installed in the past are ubuntu 7.04, and me, a
smart guy, updated to 7.10, 8.04 and finally 8.10. Are everything is
ok at users start to use the cluster again.

The configuration of cluster is a one server and eleven clientes with
two directories exported via NFS and NIS autentication between they.

The options in /etc/export are:

/home   192.168.1.0/255.255.255.0(rw)
/usr/local/cluster 192.168.1.0/255.255.255.0(ro)

And in /etc/fstab in clientes are:

ladao:/home                     /home                   nfs
tcp,sync,noatime,nodiratime,rw  0       0
ladao:/usr/local/cluster        /usr/local/cluster      nfs
tcp,sync,noatime,nodiratime,ro  0       0

But, when i have a existent arch created inside /home directory in
server and try edit this arch in exported /home directory in client
occour a permission error.

Extrange, cos, if i try only create a arch in client, the arch are
created. Thinking that, the permission to write in this directory are
correct.

look:

server:
erik@ladao:~$ ls -lnad .
drwxrwxrwx 9 1000 0 824 2009-04-08 10:30 .

client:
erik@diomedes:~$ ls -lnad .
drwxrwxrwx 9 1000 0 824 2009-04-08 10:30

But, this is the problem:

erik@diomedes:~$ touch teste1
erik@diomedes:~$ echo "aa" >> teste1
erik@diomedes:~$ more teste1
aa
erik@diomedes:~$ echo "a" > teste1
-bash: teste1: Invalid argument
erik@diomedes:~$ more teste1
erik@diomedes:~$


The archive are recreated, but cleaned.

Then, when the programs, that user are using try to edit and acces the
archies, this programs, don't work correctly.

PLEASE, SOME LIGHT HERE.

ATT.

---

### Post by zhushazang on 2009-04-13
Ah,

The filesystem on server are reiserfs ...

---

