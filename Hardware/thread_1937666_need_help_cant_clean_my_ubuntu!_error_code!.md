---
title: "need help cant clean my ubuntu! error code!"
date: 2012-03-08
forum: Hardware
---

### Post by Johannes1395 on 2012-03-08
hi i need some sericus help here :( my ubuntu can start and everything but when it comes to updating its sucks im trying to updat but the error code comes that i dont have space left and i dont have space left and i cant delete things for there it comes an other error code that i cant update it cus it dont have space left etither and then i try with terminal but the same thing there no space left ;( the full error is a bit longer down thx for reading



```
code for terminal: E: Unable to synchronize mmap - msync (28: No space left on device)
E: The package lists or status file could not be parsed or opened.  code for software center: sorry cant open software center just getting white now ;(
```

---

### Post by jerrrys on 2012-03-08
Can you get to terminal?  If so, enter:

sudo apt-get clean

That may get you enough space to get back in.

What you are going to need to do is resize your partition.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If this is a WUBI install (ubuntu inside windows) then forget everything I just posted.

Also the command in terminal to check partition is:

df

---

### Post by Johannes1395 on 2012-03-10
> **jerrrys said:**
> Can you get to terminal?  If so, enter:

sudo apt-get clean

That may get you enough space to get back in.

What you are going to need to do is resize your partition.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If this is a WUBI install (ubuntu inside windows) then forget everything I just posted.

Also the command in terminal to check partition is:

df im not an advanced user pls tell me somthing easier

---

### Post by jerrrys on 2012-03-11
Another option would be reinstall with a bigger partition.  How big is your current partition?

---

