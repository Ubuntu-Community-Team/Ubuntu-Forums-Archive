---
title: "cannot boot after remove cdrom drive"
date: 2010-02-22
forum: Hardware
---

### Post by yubyungho on 2010-02-22
cannot boot after remove cdrom drive

I had delete line about cdrom in fstab but it still freezes when I boot

I really searched every forum for the answer but I couldnt find the answer please help.

---

### Post by byStanderone on 2010-02-22
...before you removed your cd drive, did your install boot properly?

---

### Post by yubyungho on 2010-02-25
Sorry but I am quite new to linux so would you please tell me how to install booot?

---

### Post by byStanderone on 2010-02-25
...what i meant was: before you removed the cd drive, were you able to make your system operational, without this freezing problem..?

---

### Post by pizza-is-good on 2010-02-25
I may be way off in this, but maybe you have your boot priority in your bios to CD first (like most), so if there is no CD, then it goes on to boot from HDD, but if there is no CD drive then it gets lost and don't know what to do.

Try changing the bios boot order and see if that does anything.

Again, I am just guessing here...

Sorry I couldn't be of more help.

~pizza

---

### Post by yubyungho on 2010-02-26
Yes sure 

It boots with cdrom alright and cannot boot when cdrom is disconnected 

BIOS...hmmm 

I doubt that because it actually goes into ubuntu (means I can see the ubuntu logo)

and freeze

---

### Post by byStanderone on 2010-02-26
...yup, hard to say specifics at the moment, but perhaps you can verify uuid's by running a sudo blkid, and compare the results with that which are listed in your /etc/fstab. (with the cddrive removed) then edit your fstab if needed as per your blkid info.

---

### Post by yubyungho on 2010-02-26
I gedit fstab file which includes

```

#/dev/scd0    /media/cdrom0    udf,iso9660 user,noauto,exec,utf8
#/dev/fd0    /media/floopy0 auto rw,user,noauto,exec,utf8

```

put # in front of both scd0 fd0 which I dont use and devices dont exist.

problem solved but I think editing fstab isnt really only reason.

I did sudo apt-get update so it might be a soultion

---

