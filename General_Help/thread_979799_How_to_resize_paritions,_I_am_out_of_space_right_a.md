---
title: "How to resize paritions, I am out of space right after installation."
date: 2008-11-12
forum: General Help
---

### Post by cjohn106 on 2008-11-12
I just installed Ubuntu, and I had to resize Windows XP to make room for dual boot. But I only have 3G free now on an 80G HDD, all the computer's information tells me that my 80G HDD is only a 30G HDD. How did this happen and how do i get my 50G back?

---

### Post by kpkeerthi on 2008-11-12
Boot with Ubuntu Live CD. Check with System -> Admin -> Disk Partitions to see what happened to your partition. You can even resize the partitions with the tool.

---

### Post by iKonaK on 2008-11-12
So you have in xp 3 GiB free and 30 overall and you don't know where is the rest ?
In any situation go download a [gparted live cd]("http://gparted.sourceforge.net/download.php") and obviosly burn it and boot from the live cd, and there resize the way you want (if there are many files to move in the ubuntu partion, it will take a considerable time, but will eventually work)

---

### Post by cjohn106 on 2008-11-12
i had 80 gigs, with 10 being aside for a recovery partition which I was going to remove with Windows, and when i went to remove it, it was gone, but I still only have 30 gigs. I'm going to install Gnome Partition editor and give it a try

---

### Post by cjohn106 on 2008-11-14
I found out that I partitioned my two operating systems into 30G each, and I only have 3G left on the windows parition, but 27G on my Ubuntu. So I guess it worked out.

---

