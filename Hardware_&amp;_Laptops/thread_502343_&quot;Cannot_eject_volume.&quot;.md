---
title: "&quot;Cannot eject volume.&quot;"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by bdtgp on 2007-07-16
I'm running an up-to-date verison of Ubuntu 7.04 and I can't eject my external hard drive.  It hasn't been a problem thus far in terms of losing data but I do not want to continue just unplugging it.  When I try to eject it, I get the message "Cannot eject volume."

I tried this too:
```
sudo umount /dev/LaCie
```
but to no avail.  

Any suggestions?

---

### Post by jocko on 2007-07-16
are you sure "/dev/LaCie" is correct? Shouldn't it be some thing like "/dev/sdx1"?
Check the output of ```
sudo fdisk -l
``` to figure out the correct device.

---

### Post by bdtgp on 2007-07-16
thanks.  that worked.  are there any fixes on the way for the eject dialogue that we know of?

---

### Post by Bablefish on 2007-07-16
Weird thing I did have that very same problem until an update fixed it.

---

