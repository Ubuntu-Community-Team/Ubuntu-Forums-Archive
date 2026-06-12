---
title: "Need help on this Error (Initramfs) Ubuntu 10.04"
date: 2010-11-09
forum: Hardware
---

### Post by Edgar117 on 2010-11-09
Hi Everyone i get this new error today on my laptop *Initramfs*
My Laptop has no battery and my friend by accident pulled the cord and the computer got shutdown

The when i turned it back on i get this black screen which seems to be scanning all my devices but at the end when i press enter i get this *Initramfs* i dont know what to do

Can any body help me out 

Right now iam on Ubuntu 10.10 live

Thank you for your Time

---

### Post by Edgar117 on 2010-11-09
Well i guess nobody knows...

---

### Post by waterboy0911 on 2010-11-24
I have the same problem just this morning.. 

I just watch movie on my laptop then I found my desktop that all my panels are gone.. I tried to recover but it was just black screen.. I tried to hard shutdown and restart.. it was all just black and it says that mount failed..

I tried to use a live cd and I found my other file system but I can't mount them..

---

### Post by lalitpur on 2011-03-28
I know that this is an old post, but it is similar to a problem I have had and anyone searching for an answer might find this here.

Solved the initramfs error by booting into a live CD/DVD and running a disk check (fsck = file system check) on the system partition.

From the terminal: ```
sudo fsck /dev/sda1 
```

---

### Post by nancyparrishnrs on 2011-03-29
I tried to use a live cd and I found my other file system but I can't mount them..
-----
Nancy
[Payroll Solutions]("http://www.topsyssolutions.com")

---

