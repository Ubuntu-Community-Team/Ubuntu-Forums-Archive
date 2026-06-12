---
title: "change of disk"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by ykpaiha on 2006-01-10
My ubuntu-hd shows some weakness
I bought a new one.
so here come the question
How can I pass my whole root-sys and home on the new one  without any loss.'mainly rights and links.
at least keep my home with a new install ?
backup is not sufisant as the new disk is larger
old: 80go : / = 10 go (hdb1) /home/ =69(hdb2) /swap = 1 Go(hdb3)
new : 120 : / = 10 go (hdc1) /home= 110 (hdc2)......
both and all part. in reiser
at the end hdb disk will be replaced by hdc (becoming hdb) 
 

thanks

---

### Post by mips on 2006-01-10
You could always mirror the drive as an exact duplicate using the 'dd' command.

Be VERY CAREFULL though as you could erase your orinal drive if you use the command wrong.

Read up on dd befor an if you are going to use it.

---

### Post by ykpaiha on 2006-01-10
I thought already at DD command but looked very hazardous (for me of course)
Realy I was looking for an easier way to manage this.
Thanks though...

---

