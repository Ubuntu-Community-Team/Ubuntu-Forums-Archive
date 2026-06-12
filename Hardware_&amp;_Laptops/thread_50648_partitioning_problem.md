---
title: "partitioning problem"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by N'Jal on 2005-07-20
Ok guys, hear's my layout unfortunatly the installer can't seem to fix it quite how i want it, i have hda with 20GB space, master drive mount point /, 80GB hdb slave mount point /home however the problem come's when i need to add swap, since after installaion my system run's real slow, it's because i don't have any swap, now i have installed gentoo before so im not scared of using fdisk, but will ubuntu see the partition layout and use it? 

Might need a little help with laying out the partition, though i can use fdisk not quite sure the best way to do things. 

Presumably since i have 256MB ram i would create this set up: -

1)hda1 19,488MB   /
2)hda2 512MB       swap
3)hdb1 80,000MB  /home

Am i right? Any suggestions? Unfortunatly i am on holiday right now in the USA, kissismee orlando. 4211 miles away form my linux box so i wont be able to try this for another 2 and a half weeks.

I'll just save the stuff to me laptop :D

---

### Post by amohanty on 2005-07-21
That should be fine. If you have two drives I would suggest putting the swap on the non-root drive. It _seems_ to perform much better. Also I would suggest upping the swap partition to 1 GB to allow for RAM upgrades.

HTH
AM

---

### Post by N'Jal on 2005-07-23
Next question then, does the hoary installation CD have the option to format as swap? It's either 83 or 82 right?  Coz im hoping that i don't have to run the gentoo installer to set up my partitions.

---

