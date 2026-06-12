---
title: "Help I Cant Get Onto My Laptop!!!"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by alexi66 on 2007-09-15
I didnt know where to put this post so i decided its the most appropriate one...anyway, yesterday i turned on my laptop and it said a forced check needed to be carried out, but when it got to 72.2% complete it froze, i turned it off and on again several times and it still froze at either 72% or 25% and now i cant get onto it because i dont know how to skip this forced check, does anybody know what i can do?? much appreciated

xx

---

### Post by pxwpxw on 2007-09-15
Is it ubuntu and i386 doing a file system  check? A bit more info would help. 

If so, you could try starting in linux single mode.
but I don' think that will bypass the check
Next alternative is to run the installl cd in rescue mode and edit /etc/fstab to omit the check, then do it manually.

---

### Post by alexi66 on 2007-09-15
Thanks, ill try running the install cd, and im not sure what the check is but it says: /dev/sda2 has been mounted 39 times without being checked, check forced. then it freezes

xx

---

### Post by pxwpxw on 2007-09-15
Yes thats the file system check with e2fsck, see if you can post the fstab file that controls it

```

 cat /etc/fstab

```
Or if you read man fstab, it will tell you that the check is not done if the 6th (last) field is 0 or not present.

There may be an easier way, but I don't know it.

But then you will have to do the e2fsck manually.

---

