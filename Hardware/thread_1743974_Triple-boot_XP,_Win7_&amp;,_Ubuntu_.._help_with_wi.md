---
title: "Triple-boot XP, Win7 &amp;, Ubuntu .. help with windows partitions"
date: 2011-04-29
forum: Hardware
---

### Post by Image0fman on 2011-04-29
Hi All, 

I currently have a working triple-boot setup on my 320Gb Asus u80a laptop (XP,7,ubuntu). I initially used gparted to do all my partioning. I created a 10GB partition for XP, a 20GB for Win7 and about 120GB for Ubuntu, 4gb swap and the rest is still unallocated. My ubuntu partition (which I use regularly) is functioning perfectly. My windows XP and windows 7 function for a lil bit then totally lock up. They either crash (for example in a browser or doing updates) and/or completely lock up and I am forced to hard shutdown. I initially installed xp then 7 then ubuntu, I did the hide/unhide method with gparted live cd. The windows partitions can actually see each-other, w.e windows partition I am booted sees them-self as C:... does anyone have experience with this similar setup? Can grub/ubuntu be causing this issue? 

Thanks All

---

### Post by oldfred on 2011-04-29
Each operating system is separate once running. Some win7 apps have overwritten grub's boot code the the sectors just after the MBR, but that is not your issue.

How full are your windows partitions? Windows NTFS likes to have lots of free space up to 30%, at 10% they slow down a lot.

Mount your windows partitions and run this or look with gparted.
```

sudo df -H
```

---

### Post by Image0fman on 2011-05-01
Hey thanks for the reply. You know I thought disk space could be the problem.. my win7 partition has 1.5GB free and my Windows XP partition has 2.8GB free.. I do have about 100+GB of unallocated space.. you think if I make two ntfs partitions I can just span the each windows partition? or do I need to increase the size a different way?

thanks

---

### Post by oldfred on 2011-05-01
If you make a new NTFS partition, you may be able to move your data into it and still use it from both windows installs. Otherwise you have to figure out if you can houseclean a lot of old files, old software etc from Windows and/or move partitions around to make more room (usually not easy).

---

### Post by Image0fman on 2011-05-01
Yeah I guess i'll play around with it.. I mean there all brand new installs.. neither have any software installed.. so I guess ill give it a shot and see what happens

---

### Post by Image0fman on 2011-05-01
You know I was going to try "spanning" the drives in Windoze but I forgot that the disk needs to be made dynamic, which would probably really mess things up.. I think I mite re-do the entire thing again..sucks to have to lose my Ubuntu partition was getting pretty comfortable on here =/

---

