---
title: "Slow Boot Up"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by rseaward on 2006-11-15
I have Edgy Kubuntu loaded with Ubuntu and Xubuntu desktops on a sony vaio with XP already on. XP had the first 2 partitions. Then I had a partition with 4 GB on which I had Ubuntu (before I knew I could add Ubuntu onto my Kubuntu). I had 8 GB for the Kubuntu partition.

After finding out I coulod add the Ubuntu desktop, I removed the ubuntu, but could not merge the partition with kubuntu. So I had to merge it with the second XP drive.

Kubuntu was starting up within 20 seconds. Ever since I made the changes and merged the drive, reinstalle3d Grub, Kubuntu now takes atleast 2 minutes.

The bar shows it loading until it almost gets 1/2 way (about 4/10) and then it stops there. There is no more hd activity, and then a couple mintues later it continues to load and finishes in a few seconds to the log in screen.

COuld someone help me know what has made it go slow and how I can fix it.

thanks.

---

### Post by kafo on 2006-11-24
I installed linux-image-386 and linux-restricted-modules-386 and deinstalled linux-image-generic. I think edgy installs 686 kernel by default and this kernel doesn't seem to work very well on my vaio fs whereas it works very well on my desktop machine. I hope this helps.

---

### Post by jackhynes on 2006-11-24
I had exactly the same problem using a VAIO FJ (same as FS I believe), and using your fix brought the boot time from just over 2 minutes to 55 seconds (the same as it used to be in Dapper). Thanks alot.

---

### Post by Tobster on 2006-11-24
I prob not helping but does Linux use Virtual Memory if it does can you increase like in Windows because if you can that will speed up the boot up at dramatic rate

---

### Post by Tobster on 2006-11-24
Just done a Google search.  Linux does use Virtual Memory so like you can in Windows you can increase it.  But I do not know how. 

Once you increase Virtual Memory there will not be an issue with speed, just don't make your PC run to fast that it can't keep up with it self,  if you do  you can decrease the Virtual Memory.

I hope this put you on the right road.

Toby

---

