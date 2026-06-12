---
title: "Install drivers???"
date: 2011-03-22
forum: Hardware
---

### Post by hopkinskong on 2011-03-22
Hello,
 
I got few .so library, and i think it was drivers(are they? or driver should in another special location???), how to install them? Just copy to /lib?
 
 
Thanks.

---

### Post by hopkinskong on 2011-03-23
help! No one helps?

---

### Post by Yellow Pasque on 2011-03-23
What are these .so files? If you're writing them to /usr/lib, they should be in a .deb file.

---

### Post by hopkinskong on 2011-03-24
I am trying to port a program to my device, it was ARM, and i have copied another devices drivers to try to use on my device.
 
The another device also was ARM, and i think it should work on my device!
 
And those (diivers? may be?) are on the /lib, i extracted them, and trying to use on my new device

---

### Post by Yellow Pasque on 2011-03-24
So they're kernel modules? You'll probably need to get the source and compile it against your current kernel or you'll get "vermagic" errors..
..but yes, kernel modules go in /lib/modules/<kernel version> and then you run:
```
sudo depmod -a
```

---

