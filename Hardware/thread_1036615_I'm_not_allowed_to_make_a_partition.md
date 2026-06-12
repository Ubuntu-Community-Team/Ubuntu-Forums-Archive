---
title: "I'm not allowed to make a partition?"
date: 2009-01-11
forum: Hardware
---

### Post by darkjaksrevenge on 2009-01-11
Hey guys, I need some help.

 I just want partition my HDD. I'm on Vista and when I go into disk management it says I have 108GB available..

So when I go and do add "New Simple Volume" it only allows me to make a  6GB Parition . Some people get this problem as I google'd it..

Anyways, if I have enough space to make a partition bigger than 6 GB why won't Vista let me make something bigger? 

Yes, I am doing this via My Computer<Manage< Disk Management.

It only let's me make a 6GB Partition..

 I tried some program it made the allocated space and then when it was formatting it got an error and everything reversed I guess, I used GPARTED and got an error for some reason. 

 I have no idea what's up guys, please help!!

---

### Post by blackened on 2009-01-11
You can only create new partitions in unallocated space. So if your Vista partition is taking up the entire drive, then it doesn't matter if there's any actual data stored in that section or not, it is still allocated to the Vista partition.

Shrink your Vista partition by a reasonable amount, then create a new partition in the now unallocated space.

---

### Post by Sef on 2009-01-11
You have to use Vista's partitioner to create the new partition.

---

### Post by darkjaksrevenge on 2009-01-11
> **blackened said:**
> You can only create new partitions in unallocated space. So if your Vista partition is taking up the entire drive, then it doesn't matter if there's any actual data stored in that section or not, it is still allocated to the Vista partition.

Shrink your Vista partition by a reasonable amount, then create a new partition in the now unallocated space.

That's kinda stupid, is there any way to add more "Unallocated space"? 

@Sef: I'm using Vista's Partitioner.

---

### Post by darkjaksrevenge on 2009-01-11
Also here is a screenie

[IMG]http://img53.imageshack.us/img53/9365/problembx8.jpg[/IMG]

---

### Post by ajcham on 2009-01-11
> **darkjaksrevenge said:**
> That's kinda stupid, is there any way to add more "Unallocated space"? 


It's not stupid at all.  In fact, it is exactly what you are asking how to do. The space is currently allocated to Vista, so you need to do what was suggested and reduce the size of the Vista partition, which will increase the size of the unallocated space.

---

### Post by darkjaksrevenge on 2009-01-11
> **ajcham said:**
> It's not stupid at all.  In fact, it is exactly what you are asking how to do. The space is currently allocated to Vista, so you need to do what was suggested and reduce the size of the Vista partition, which will increase the size of the unallocated space.


How do I reduce the size of the vista partition?

---

### Post by ajcham on 2009-01-11
> **darkjaksrevenge said:**
> How do I reduce the size of the vista partition?

I would have advised GParted from a LiveCD, but Sef indicates that you have to use the Vista partitioner.  I don't know Vista, so I don't know why this is the case, but I'll defer to Sef's judgement and assume that there is some problem with using GParted for this task. I guess it must be related to NTFS.

Maybe someone else will be able to guide you through using the Vista partitioner.

---

### Post by darkjaksrevenge on 2009-01-11
ok thanks.

---

