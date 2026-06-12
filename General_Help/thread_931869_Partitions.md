---
title: "Partitions"
date: 2008-09-27
forum: General Help
---

### Post by malel on 2008-09-27
I am running Ubuntu 8.04 which is on the whole HDD but when I downloaded Fedora 9 iso and tried to install it, it said it did not recognise the disk space . I am quite sure it is formated as ext3 with a swap partition. Any help would be appreciated 

Thank you

---

### Post by ajmorris on 2008-09-27
> **malel said:**
> I am running Ubuntu 8.04 which is on the whole HDD but when I downloaded Fedora 9 iso and tried to install it, it said it did not recognise the disk space . I am quite sure it is formated as ext3 with a swap partition. Any help would be appreciated 

Thank you

Hi there,
you can check the format of the partition via a partition editor such as gparted.
When you say Fedora 9 said it didnt recognise the disk space, what partitioner in Fedora were you trying to use to resize the partition to make room for fedora?

AJ

---

### Post by zvacet on 2008-09-28
You can not install anything because your whole Hd is dedicated to Ubuntu.You have to make some space to another distro.With [Gparted live CD]("http://gparted.sourceforge.net/") you can shrink your ubuntu partition and on unallocated space install Fedora.

---

### Post by malel on 2008-09-28
Thank you to everyone who replied to my thread.
I have fixed the problem now .
I used the live Ubuntu CD and the disk partitioner inside it and now I have both
Ubuntu and Fedora running 
This thread can be considered closed now

---

