---
title: "Harddisk is full -How do I  clean up uid's ?"
date: 2009-04-11
forum: Hardware
---

### Post by racoope on 2009-04-11
Hi,
I have a  new Maxtor 135GB harddisk , running Intrepid (Ubuntu) of  which about 60GB was used.
I recent attempted to (unsuccessfully) rsync to a  Buffalo external disk NAS disk device   and for    some reason,     my local harddisk filled up  with no  space   left.
 Can anyone advise where I can find the offending directories  using  up  so much  space ? I  think it may be  in the root directory under UID's ?
Any help or suggestions, greatly   appreciated.
Thanks,
racoope

---

### Post by cariboo on 2009-04-11
You look in the /root directory twoo ways, the gui way, press Alt-F2 and type:

```
gksu nautilus
```

the above command will start the file manager in /root. The fast way, open a Applications-->Accessoreis-->Terminal and type:

```
sudo -i
```

and enter your password, you will now be in /root.

Jim

---

### Post by racoope on 2009-04-13
Thnaks Cariboo907,
When I get to root and see the UID's, I have one UID in UID-1000 (user created) that has over 11,000 entries for the  day., What happens if  I delete this (to save space). Actually, what are UID's ?

Appreciate  your information.

Thanks,

racoope

---

