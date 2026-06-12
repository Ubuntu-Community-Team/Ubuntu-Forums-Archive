---
title: "Remove XP from Grub"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by owen1 on 2009-03-10
I was dual booting XP and ubuntu, but i have now completely wiped XP from the hard Drive using Gparted and just made he unpartitioned space NTFS to store data on. 

So now i have a few questions: 

1.) Xp still comes up on the Grub menu, is there a way to remove it? it's not that big of a deal really, but might as well get rid of it if i can

2.) is there a way using Gparted or other to increase the size of the partition ubuntu is installed on, because in "Filesystem" it says i only have 17 gig remaining, i don't think i give it enough in the first place. 

When i did what i thought was resizing it it just gave me another empty drive of the 22gig (Hope you know what i'm trying to accomplish and what i did wrong) 

Thanks for the help, still learning to use ubuntu to it's fullest.

---

### Post by Neo_The_User on 2009-03-10
Go in menu.lst and delete all the windows lines as root.

---

### Post by owen1 on 2009-03-10
Thank's, think i have done it, will reboot to check. 

is it also safe enough to edit the boot option time thing, it's now at 10 seconds good i change that safley enough to say 4 or 5? And other things such as the names of the aplications. Such as change the one that loads ubuntu to simply ubuntu? Again not that important, just curious really 

Thanks.

Now what i want to attempt to do is to increase the "Filesystem" Drive i have, it currently only has 17 gig and i wasn't sure if this was enough to have spare, i have a screenshot from Gparted.

[[IMG]http://img175.imageshack.us/img175/9504/screenshotdevsdbgpartedh.png[/IMG]](http://img175.imageshack.us/my.php?image=screenshotdevsdbgpartedh.png)
[[IMG]http://img175.imageshack.us/img175/screenshotdevsdbgpartedh.png/1/w775.png[/IMG]](http://g.imageshack.us/img175/screenshotdevsdbgpartedh.png/1/)

What i want to  do is extend the filesystem into the "Unallocated" space, but im not sure how to go about doing it, or if it's even worth doing.

please let me know.

Thanks

---

