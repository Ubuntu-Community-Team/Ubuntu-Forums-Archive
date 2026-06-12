---
title: "Can't Write To CD-RW Drive"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by ebozzz on 2007-03-30
I installed a second optical drive, Creative CDRW, on one of my desktops as a slave. It plays discs just fine but when I attempt copy to that drive, for example an ISO disc, it will not allow me to write to it. When I checked the properties for that drive I discovered that were set to read only. Any attempts to change the permissions to read and write get the following error message:

> **The permissions could not be changed.**
Sorry, couldn't change the permissions of "CD-RW Drive".

Can someone *please* point me in the right direction to correct this issue? Thanks!

---

### Post by ishmeetahuja on 2007-03-30
hey...

seems its a rights problem..


why dont u intialize the burning program by issuing root command like...

if u r burning the cd with k3b .. instead of starting the application by menu .. go to terminal and write 

```
sudo k3b
```

enter ur password and then try...

try it...

good luck

---

