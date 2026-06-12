---
title: "activating second swap partition on seperate hard drive"
date: 2008-07-16
forum: General Help
---

### Post by bobaffett on 2008-07-16
I have just recently installed ubuntu server edition 8.04 on my old Pentium III server. I could not get sofware raid to install soo I partitioned the hard drives seperatley ending up with the same image on both hard drives. meaning I have an extra 450mb of swap is there any way I can utalize this swap partition as well?

---

### Post by scragar on 2008-07-16
```
swapon /dev/sdb**x**
```
where sdbx is your swap partitions name.

for a change that isn't lost on a restart you'll need to edit the fstab, but wait till you get it working temp first before making that change(since mistakes are more persistant)

---

### Post by bobaffett on 2008-07-16
the output says cannot stat no such file or directory

---

### Post by bobaffett on 2008-07-16
Actually wait I had a typo no I am getting the real error swapon: /dev/sdb2: invalad argument

---

### Post by scragar on 2008-07-16
then that's not the right partition :P

```
sudo fdisk -l | grep swap
```

---

### Post by bobaffett on 2008-07-16
Ok... here is the output for what I tried  

/dev/sda5            1054        1106      425691   82  Linux swap / Solaris
/dev/sdb5            1054        1106      425691   82  Linux swap / Solaris
bobaffett@server-old:~$ swapon /dev/sdb5
swapon: /dev/sdb5: Operation not permitted

---

### Post by scragar on 2008-07-16
try ```
sudo swapon /dev/sdb5
```
to be quite honest I've not used swapon/off for a while, so I kinda forgot if it needed root perms or not(didn't want to say to use them incase I was wrong and it'd risk some security).

Oh, and edit your fstab to add it in before I forget:
```
gksudo gedit /etc/fstab
```
add```
/dev/hda5        none      swap    sw     0       0

```
somewhere neer the end(You should have your current swap in there as a guide anyway)

---

### Post by bobaffett on 2008-07-16
Its working. thanks a ton.

---

### Post by jbeukema on 2009-08-22
I I install Ubuntu on one drive that has no SWAP partition and there is a SWAP partition on a second drive, will it use it? Would there be any significant performance gain from doing such a thing?

---

### Post by P4man on 2009-08-22
> **jbeukema said:**
> I I install Ubuntu on one drive that has no SWAP partition and there is a SWAP partition on a second drive, will it use it? 

Yes;

> Would there be any significant performance gain from doing such a thing?

No. I dont know how much ram  you have, but I got 2 gigs, and I pretty much never need any swap at all, except perhaps for hibernate. Are you using a lot of swap? Keep in mind, linux uses swap differently than windows. Windows will always swap, no matter how much (free) ram you have, it will swap and use the freed RAM as cache. Kinda silly really. Linux is a lot less "swappy", and only swaps when its needed.

---

### Post by scragar on 2009-08-22
> **P4man said:**
> Yes;



No. I dont know how much ram  you have, but I got 2 gigs, and I pretty much never need any swap at all, except perhaps for hibernate. Are you using a lot of swap? Keep in mind, linux uses swap differently than windows. Windows will always swap, no matter how much (free) ram you have, it will swap and use the freed RAM as cache. Kinda silly really. Linux is a lot less "swappy", and only swaps when its needed.

Unless you change the swappiness :p

It's set to 10 by default on most linus systems, decrease it and you'll use less swap normally, increase it and you'll use more swap normally(reserving more for cache). Personally I only see a need to change the value if you're experiencing serious problems.

---

