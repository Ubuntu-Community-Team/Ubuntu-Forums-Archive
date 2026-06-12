---
title: "Wrong format?"
date: 2009-03-14
forum: Hardware
---

### Post by berryboy on 2009-03-14
hello, Im very new to ubuntu, having just switched from MS, 
everything seems to be going just fine apart from one thing.
i had a USB hard drive formated in windows format (ntfs).

so i got Gparted and formated it to ext3 ? 

heh now the drive no longer shows up,
I used to be able to see it in "computer" labled as "elements" although i could not view it due to htfs, i'v read various topics and even been reading ubuntus built in help, should'nt it display in the pannel and then from there right click and select mount? 
did i use the right format? 
also Gparted can still see the drive in devices menu

some pointers would be real helpful here :) 

thank you for your time!
BB

---

### Post by taurus on 2009-03-14
Make sure the drive is on and plugged in.  Then, open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by berryboy on 2009-03-14
thank you for your time, seems all it needed was an update and a reboot but thank you very much for responding, 
but now i can see it on my pannel, but i can not mount it.
giving this error

```
Error org.freedesktop.DBus.Error.AccessDenied.
```

been doing some searching it maybe that i need to add my user account to 'storage' group, but i can not find a guide on how you do that o_0 . 
also if anyone has any good site/s which can help me brush up on ubuntu please post them, i need to read as much asposs on this subject, 

again thank you 
BB
ok i made a folder on the drive using gksudo nautilus, then set permissions for my account :) all fixed !

---

