---
title: "rc.local script problem"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by wimmelis on 2009-08-21
Dear all, 


Fairly sure this is something really silly, but I do not manage to catch it :(.
I have a service that needs to start together with the machine. So, I added a line to /etc/rc.local, but to no effect. 
The file mentions that for it to work, you have to change the execution bits. When checking the file permissions then x is set for all three (user, root, group) but when I run it, it does not seem to work. 
Are there some other execution bits somewhere ?


Thanks, 

WM

---

### Post by enli on 2009-08-21
Execution permission is different and owership permissions are different. To make any file executable, right click > Properties > Permissions tab > At the bottom Permissions checkbox.

Simple fix,
```

chmod a+x /etc/rc.local     (this will make rc.local executable by all users)

```

---

### Post by wimmelis on 2009-08-23
Dear enli, 


This was actually what I tried to say, that all the x's were set, since you have them in relation to the ownership. The first set of characters in the row when you do an "ls -al".
So, since this is already the case, there must be something else that's wrong. Anyone ?


Regards, 

WM

---

