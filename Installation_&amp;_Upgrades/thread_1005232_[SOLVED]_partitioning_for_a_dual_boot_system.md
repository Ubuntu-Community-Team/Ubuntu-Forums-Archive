---
title: "[SOLVED] partitioning for a dual boot system"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by vbrocz on 2008-12-08
i'm totally new to linux. so i'm trying to install ubuntu alongside windows. if choose to partition manually and install linux in 1 of my primary partitions, will it destroy the data on other 2 primary partitions in which i have my important data?

---

### Post by sukhhari on 2008-12-08
No, it will not destory any data, you can install on logical partition.

---

### Post by vbrocz on 2008-12-08
Thanks for your reply.

i have 1GB of ram.do i need to have a swap partition?

what are the logical partitions i need?
i have 31GB free for linux.

---

### Post by MobiusNZ on 2008-12-08
Ubuntu is very flexible... with your ram you only really need a / (root) partition. BUT if you want to run more programs at once, a swap partition might be a good idea (especially if you have 30gb free anyway). Usually you make it around about the size of your memory.

Other partitions are completely optional - if they don't exist in their own right, they just go in your / partition.

Many people (like me) consider it useful to have a /home partition. This is kind of like the Documents and Settings/Users folder on Windows - it stores all your profile information, documents, pictures and the like. If you create /home as a separate partition then if you ever re-install linux you don't have to loose your documents or settings.

You'd usually only create other partitions if you had a good reason to (eg a /var partition for web servers etc)

---

### Post by glotz on 2008-12-08
The simpliest setup only features a root (/). Some people prefer a separate /home partition. I'm not sure about how big they should be if you go for that setup.

Since with newer kernels swap files are supposed to be just as fast and swap partitions I think you're better off without a swap partition. You can make the file later and tune the swappiness setting if needed.

EDIT: here's a couple of guides for partitioning, though they are a bit dated
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

and here's a good reading on the swap issue [https://wiki.ubuntu.com/SwapFaq](https://wiki.ubuntu.com/SwapFaq)

---

### Post by vbrocz on 2008-12-08
thanks all for being so helpful.
:lolflag:

is it necessary to specify mount points for all the other partitions, to access them through Ubuntu?

---

### Post by glotz on 2008-12-08
You're welcome and ****

EDIT: misleading help removed... Sorry!

---

### Post by vbrocz on 2008-12-08
does that mean that i have to mount those partitions to /etc/fstab in the partition program of Ubuntu?

---

### Post by glotz on 2008-12-08
No sorry! I wasn't thinking clearly. During partitioning, only touch the partitions you want to use for Ubuntu. The windoze partition can be mounted later once you have installed. Hope you didn't do anything rash because of my misleading help...:oops:

---

### Post by vbrocz on 2008-12-10
oh itz ok........ i installed linux without any trouble.

i'm still searching for some trouble..........:p

thankz!

---

