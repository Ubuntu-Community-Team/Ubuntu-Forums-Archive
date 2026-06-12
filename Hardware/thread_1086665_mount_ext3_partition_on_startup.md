---
title: "mount ext3 partition on startup"
date: 2009-03-04
forum: Hardware
---

### Post by redruby on 2009-03-04
Hi.

I have been trying to get my large partition to mount at startup, but i am finding it hard to get an exact description of how to do that. The partition is an ext3, below is a list of my partitions.

/dev/sda1   ext3/              7.81GiB
/dev/sda2   extended          66.72GiB
  /dev/sda5 linux-swap         3.90GiB
  /dev/sda6 ext3  /media/disc 62.82GiB

Ubuntu sits on sda1 and everything works well, it is just that I would like to have sda6 available from startup.

I tried editing fstab to get it going but it didn't mount

many thanks

---

### Post by logos34 on 2009-03-04
try [this guide]("http://www.psychocats.net/ubuntu/mountlinux")

hope it helps you

---

### Post by redruby on 2009-03-04
many thanks logos34. however much i searched on the web i didn't find anything as helpful looking.i will have ago at that,

i will post my results

incidentally your link was doubled up:-)

---

### Post by redruby on 2009-03-06
Yes. That worked, all is running as it should.A few hiccups along the way. I have learned some useful stuff.

Thank you logos34

---

### Post by logos34 on 2009-03-06
my pleasure

enjoy ubuntu!

---

