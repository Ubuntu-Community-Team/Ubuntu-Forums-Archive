---
title: "Boot problem grub error 17"
date: 2008-11-29
forum: General Help
---

### Post by sklipnoty on 2008-11-29
Hello,

I have a problem with booting, 
it all started yesterday evening,
I was cruising on XP and saw that I had to much stuff on my HDD's 
( Got internal - 250 gig and external harddrive 500 gig ) 
Other then that you ought to know that I have a double boot ( Linux-ubuntu 8.X and Xp MCE ) 

So I deleted a partion ( 50 GIG ) and then formatted it, to get more space basically. Not knowing that this partion was a part of my linux boot ? Or at least I think so, file swap system or the other thing. 
Anyway I tried booting from Ubuntu CD and formatting every lose partion except for my XP and re-installing Linux, but that didn't work.

Every time I boot now,
I get the error:

GRUB Loading stage1.5.

GRUB loading, please wait....
Error 17


Any help on this is greatly appreciated.

My regards,

Axl

---

### Post by caljohnsmith on 2008-11-29
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

