---
title: "Duplicity cant find files"
date: 2008-11-07
forum: General Help
---

### Post by Roosta21 on 2008-11-07
Hi I've installed Duplicity to back my computer to an external server, i've followed the instruction to the letter.

Set up ssh keys etc.. all thats fine

I run duplicity (command below) it seems to run fine backs up and will even restore if you delete the director and run restore..

..but i cant find any files anywhere!! on either server to indicate a backup has taken plan

i've used locate (after running updatedb) ls -all

duplicity /root/backsource scp://root@217.XXX.XXX.80/root/duptest2

---

### Post by Roosta21 on 2008-11-10
bump

---

### Post by karlh626 on 2008-11-11
try searching for files that end with .gpg

your command:

duplicity /root/backsource scp://root@217.XXX.XXX.80/root/duptest2

does not have 2 "//" after the destination ip address

When I use duplicity it contains two slashes after the ip of the destination server.

---

