---
title: "Omdat ik op dit ogenblik actief uitkijk naar een nieuwe professionele uitdaging ben i"
date: 2009-09-10
forum: Hardware
---

### Post by deboopi on 2009-09-10
Hello,
I heard so much good about linux that I want to give it a try on my new netbook.
So first of all I installed the windows XP Home
Beccause of the necessity of a swap drive I did repartition the system
I left the two smaller partitions as they were but repartitioned the two biggest partitions
The primary C was split into a 50 and a 30 Gb partition
The primary D became a logical 50 and logical 30 gb because I could not make them primary when repartitioning.
I installed Ubuntu jaunty NBR on the second 50 gb partition with the second 30 Gb partition as swap.
Ubuntu runs well but I have problems booting up windows xp
When I boot windows it starts reinstalling win xp home from the hidden partition, reboot a second time and yes, it starts installing win xp home once more.
So I think the ubuntu multi os booter points to a wrong partition, 
how to solve this?
 
Regards

---

### Post by barnex on 2009-09-10
Although I cannot tell how to fix the windows issue, I have one tip: if you need to repartition for some reason, take a waaaaay smaller swap partition. About twice the size of your RAM should be sufficient.

---

### Post by deboopi on 2009-09-10
I hears that one before , but I am new to Linux so I did not know what the swap area ws fore.
But thus still does not elp me on solving my problem

---

### Post by P4man on 2009-09-10
Have a look at the grub configuration file:

```
gksudo gedit /boot/gub/menu.lst
```

Find the entry for XP. It will probably contain a line like
```
rootnoverify (hd0,0)
```

hd (0,0)  means first harddisk, first partition. Change it hd (0,1).

If it doesn't work, post the the contents of your menu.lst as well as the output of this command:

```
sudo fdisk -l
```

BTW: whats up with the thread title lol?

---

### Post by deboopi on 2009-09-10
I'll try that one.
The title: well i copied from the wrong page, the title is in Dutch but I resent the thread with a correct title
 
cheers

---

