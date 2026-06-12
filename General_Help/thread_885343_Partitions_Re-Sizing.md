---
title: "Partitions Re-Sizing"
date: 2008-08-10
forum: General Help
---

### Post by zachoeser on 2008-08-10
When i installed Ubuntu i but it on a 10 gig partition. Now i have decided i want to make it bigger. i have a empty 10 gig (partition) that is not being used. How can i expand ubuntus partiotion to that extra 10 gigs. I have tried partition magic, gparted on ubuntu and the disk manager on windows. none of them will let me access or change the others partition size. Please and thank you for the help

---

### Post by cdtech on 2008-08-10
You'll need to use the "[[COLOR="DarkRed"]gparted live cd[/COLOR]]("http://gparted.sourceforge.net/livecd.php")". Boot from the cd then delete the extra partition and then expand the ubuntu partition into the extra space.

Hope this helps.......

---

### Post by zachoeser on 2008-08-10
i have tried downloading the gparted live cd multiple times. from sourceforge and download.com and it will not for some reason burn onto my cd's i have tried 2 different type of iso burning programs (power and magic ISo) and neither works!

---

### Post by doas777 on 2008-08-10
gparted is on the ubuntu live cd as well, so mabey that will work for you.

hope that helps,
Franklin

---

### Post by zachoeser on 2008-08-10
i have the ubuntu cd i got in the mail, so what your saying is if i run that as the live cd option it should work with gparted?

---

### Post by cdtech on 2008-08-10
Yes, thats correct.

---

### Post by redjoel on 2008-08-10
> **zachoeser said:**
> When i installed Ubuntu i but it on a 10 gig partition. Now i have decided i want to make it bigger. i have a empty 10 gig (partition) that is not being used. How can i expand ubuntus partiotion to that extra 10 gigs. I have tried partition magic, gparted on ubuntu and the disk manager on windows. none of them will let me access or change the others partition size. Please and thank you for the help

we are having the same problem bro!! thanks for the answers
Bravo UBUNTU!!:guitar::lolflag::popcorn:

---

### Post by zachoeser on 2008-08-10
'

---

### Post by zachoeser on 2008-08-10
> **doas777 said:**
> gparted is on the ubuntu live cd as well, so mabey that will work for you.

hope that helps,
Franklin

so far i got to what you were talkign about but the problem is the un allocated are is at /dev/sda1 and my ubuntu is at /dev/sda3
how do i move the 10 g of unallocated down to the sda3

---

### Post by doas777 on 2008-08-10
that is more of a problem I'm afraid. I did a bit of googleing, and people are saying that gparted requires the resizable areas to be contiguous, though i can't swear to this myself.

one thing you may try, is create a new partition in the unallocated space, and move teh data on sda2 to it. then delete sda2 and resize sda3 to encompass the area that used to be sda2 and 3.

I'm sorry I can't gaurentee that that will work, but it may be worth a try. 

also you may want to look into just mounting the unallocated space to a point on your / partition. do you really need to expand the root, or could you just mount space to a new folder?

good luck and have fun.
Franklin

---

