---
title: "Bad Graphics on old Laptop"
date: 2008-07-16
forum: General Help
---

### Post by ckrp25 on 2008-07-16
Tried running Ubuntu on an older laptop, but the screen is all messed up and it looks like part of the desktop repeats itself and there are a few lines going down the middle.  I assume its some kind of resolution problem, but ive attached a picture of what it looks like.  Thanks to anyone who knows how to fix this.

---

### Post by ckrp25 on 2008-07-16
Bump

---

### Post by jonian_g on 2008-07-16
When the LiveCD starts, after choosing your language, hit F4 and choose "safe graphics mode". Might work.

---

### Post by ckrp25 on 2008-07-16
Yeah I tried that for some reason the same thing happened...

---

### Post by jonian_g on 2008-07-16
Then try installing ubuntu from the alternate cd. The livecd is reported to have, sometimes, problems with older hardware.

---

### Post by ckrp25 on 2008-07-16
what is "the alternate cd"

---

### Post by jonian_g on 2008-07-16
Alternate cd has a text installer.

Info here:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Download it from here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the checkbox under the "Start Download".

---

### Post by tamoneya on 2008-07-16
the alternate CD should work well for you.  If it doesnt get into terminal and type ```
lcpci
``` and paste the output here.  That way we figure out what your graphics card is and help you install whatever drivers you need and fix xorg as necessary.

NOTE: you may want to write the output to a file like this```
lspci > output.txt
```That way you can write it to a usb key and then post it on the forum via another computer.


EDIT: Please dont bump for at least 24 hours.

---

### Post by ckrp25 on 2008-07-17
Weirdly enough, I tried xubuntu and it worked.. maybe it was that i was using an older version of ubuntu.

---

