---
title: "vista HDD partiton"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by CrimsnDragn on 2008-12-16
so i was trying to partition my C: for ubuntu to install. for some reason, i right click in disk manager and select shrink, a message pops up that says i don't have enough memory. Several things i find weird about this:

-3gigs of ram should be enough
-I even closed some big memory hogging apps, like sidebar, all the windows, even explorer.exe itself
-i have done this before, just 2 weeks ago, to install ubuntu (i had to uninstall for technical reasons), and it was working fine.

any help i could get with this? thanks!

---

### Post by Yathi on 2008-12-16
U can shrink the partitionn by using Gparted in the live CD of ubuntu. Tat should be a better method to do it. Then u can install ubuntu straight away. N by memory i think it means the HDD memory n not your ram. I m myself new to ubuntu but have done a lot of installations for my friends.

---

### Post by Partyboi2 on 2008-12-16
For Vista you are better off to use the resize tool that comes with vista. If you are having problems with memory then check your  virtual memory size in Control Panel> System and Maintenance>Performance Information and Tools> Advanced Tools. Another thing you could do is boot a ubuntu live cd and at the main menu choose "memtest" and check your ram.

---

### Post by falcon61102 on 2008-12-16
Just a tip for resizing: 
It's always wise to defrag your drive a few times to ensure the most amount of free space is in one block.  That will help prevent against data loss during the resize.

---

### Post by Mark Phelps on 2008-12-16
When you're running Vista, you can't shrink the "C" drive.

Also, do NOT use GParted or any other Linux tool to try to shrink that partition.  Vista does some weird stuff with NTFS and if you use a Linux tool to shrink the OS partion, that will most likely "break" it.  If you have a Vista DVD or Vista Recovery CD handy, you can then boot using that and do a Startup Repair to get Vista booting again.  But if you don't have those, you run the risk of permanently "breaking" Vista.

---

### Post by CrimsnDragn on 2008-12-16
> **Mark Phelps said:**
> When you're running Vista, you can't shrink the "C" drive.

Also, do NOT use GParted or any other Linux tool to try to shrink that partition.  Vista does some weird stuff with NTFS and if you use a Linux tool to shrink the OS partion, that will most likely "break" it.  If you have a Vista DVD or Vista Recovery CD handy, you can then boot using that and do a Startup Repair to get Vista booting again.  But if you don't have those, you run the risk of permanently "breaking" Vista.

you can't shrink the C drive?


hm idk, my only problem is that i want to shrink it, and i've done it before in what i perceive to be the same conditions, and i can't anymore..

---

### Post by Partyboi2 on 2008-12-16
> **CrimsnDragn said:**
> you can't shrink the C drive?


hm idk, my only problem is that i want to shrink it, and i've done it before in what i perceive to be the same conditions, and i can't anymore..
Yes you can shrink the Vista partition,  What size is your vista partition and what size are you try to resize it to?

---

### Post by CrimsnDragn on 2008-12-16
total of 140 gig, 90gig free, want 10 gig free for ubuntu. idk..i thought i had enough space...

---

### Post by Partyboi2 on 2008-12-16
Have you defraged windows a couple to times first?

---

### Post by CrimsnDragn on 2008-12-16
i did it 3x with the one that came iwth vista...i'm running auslogics now.

---

### Post by CrimsnDragn on 2008-12-16
didn't work...still. is there any free partition managers i could try instead?

---

### Post by Partyboi2 on 2008-12-16
If you are using 32bit vista you could try
 [[COLOR=Blue]EASEUS Partition Manager [/COLOR]]("http://www.partition-tool.com/")or
[[COLOR=Blue]Acronis[/COLOR]]("http://www.acronis.com/homecomputing/download/diskdirector/")

---

### Post by Mark Phelps on 2008-12-17
Sorry for any misinformation on my part -- of course, you CAN shrink (or at least, TRY to shrink) the Vista OS partition.

Here's a link to the How-to-Geek page on that with some hints of stuff you can try that will help you shrink it more than the feeble amount that Vista typically permits:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by CrimsnDragn on 2008-12-17
thanks guys! EASUS did the trick..made a scary looking boot screen after the restart but it seemed to ahve worked and i installed 8.10. now i have to get my ath5007 workign :(

---

