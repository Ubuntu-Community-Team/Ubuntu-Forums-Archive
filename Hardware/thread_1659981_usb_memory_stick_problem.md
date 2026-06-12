---
title: "usb memory stick problem"
date: 2011-01-04
forum: Hardware
---

### Post by danny_t33 on 2011-01-04
Hey, I'm new to ubuntu, using 10.10

When I plug in my usb memory stick it comes up; Error: Unable to mount, error creating mount point: no such file or directory. I tried formatting it but made no difference

thanks

---

### Post by sam1948 on 2011-01-14
[[COLOR="Blue"]_this_[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10183758") one helped me.

try this:

open command line.
run this:
```
cd /media
```
if the result looks like this:
> bash: cd: media: No such file or directory
or similar 
then this is the solution:
```
sudo mkdir /media
```

otherwise its another problem. write here if u will need further help.

---

### Post by sam1948 on 2011-01-14
i sent twice. please ignore this one(:

---

### Post by sam1948 on 2011-01-14
how do i delete messages from that were post by mistake ?

---

