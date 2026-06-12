---
title: "Buffer I/O errors on sdb"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by gasparov on 2005-05-25
Hi,
   do you know a guy called Murphy???Well I do now....
After copying files from the LAN i got an error and the device got remounted read-only, after reboot I found out that that device is full ,I repeat full of buffer I/O errors.It's an ext3 partition and it takes ages clicking yes every time fsck finds and error (-p,-a doesn't work),even beacuse the main problem is that it's a 150Gig partition (biggest)full of music and vids.I do can mount the partition and data is still there , mpayer plays vids and xmms palys music but there are errors in fs anf it's never a good thing.
First off all I don't have a clue why this a problem ,I used gparted a week ago and used the computer often since without problems.I don't know what happend ...
Does someone could give me a tip on how deal with this problem, considering the fact that I'm afraid of making fsck correct all those errors by the way data is not corrupted totally now...
Could someone point me out other tips for preventing this from happening?As a noob i thought that having ax ext2 fs with journal (that is ext3) was enough...big mistake...

Murphy ....why didn't you kill my ntfs partition \\:D/ ? and most important why the hell when I have such problems on my desktop,ipw2200 on my laptop doesn't work properly,is everyone against me  ?

---

