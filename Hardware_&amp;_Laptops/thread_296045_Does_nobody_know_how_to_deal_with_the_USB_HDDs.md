---
title: "Does nobody know how to deal with the USB HDDs?"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by lovloss on 2006-11-09
Im working in Edgy Eft, and I have been using this USB HDD for some time. Now, all of a sudden, it wont mount until i turn it off and turn it back on during bootup at the moment where it freezes. It seems to me that its not mounting correctly

---

### Post by givré on 2006-11-09
Hi lovloss,

Some question :
Did you set your usb hdd in fstab ? You probably know that you don't always have to, and it's even recommended to not do so.
How is it freeze, is it a complete freeze ?

---

### Post by lovloss on 2006-11-09
It freezes as though its waiting for me to turn it off and on... :(

---

### Post by givré on 2006-11-09
You didn't answer my first question ;)
For the freeze, you may have a look at dmesg |tail to know what's wrong.

---

### Post by lovloss on 2006-11-09
Ah well, you see... fstab... i dont really know what that is o.o  Linux is actually *on* it. c.c

---

### Post by givré on 2006-11-09
Ok, can't help more if you can't help me.
Have a good day (or night, depending on where you are) .

---

### Post by lovloss on 2006-11-09
Ok how do i check what the fstab is

---

### Post by givré on 2006-11-09
********** Wha, double post

---

### Post by newlinux on 2006-11-09
```
more /etc/fstab
``` - you might want to post the contents (minus any sensitive information).

---

### Post by lovloss on 2006-11-09
Thanks guys. When i get home ill post whatever i got :)

---

### Post by lovloss on 2006-11-09
Okay I did the fstab thing.
Here's what it said about the two partitions of my external:

the first partition is ext3, where Ubuntu is. I got:

# /dev/sda1
/
defaults,error  
s=remount-ro 0       1


The second one is ext2 and it's for storage:

# /dev/sda3
/home
defaults      
  0       2


I see "error" and "s=remount -ro 0" as potential issues. Any ideas?

---

