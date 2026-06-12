---
title: "mkinitrd not working"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by IronWolve on 2005-10-24
Anyone else notice mkinitrd isnt working? Tried two generic installs, and when I try to make an initrd.img, it doesnt make the image. I do see its copying the files to /tmp, it just doesnt creat the finished file.

Is there something different in unbuntu about mkinitrd?

---

### Post by georgek on 2005-10-30
Just found your post.  If it's not too late, I'm also trying to create a new initrd.img with other problems (but I won't hijack your thread).

First time I ran it, it complained about missing /lib/libdevmapper.so.1.00.  Now when I looked to see what I had, it was version 1.01 so I just edited /usr/sbin/mkinitrd and changed the lib version and it ran without complaint.

I guess if you're using mkinitrd you'd probably notice any errors you got, but just in case ;)

---

### Post by AlexBligh on 2005-10-30
It did the same here, but I solved it by passing a full path to -o, i.e.
[INDENT][FONT="Courier New"]mkinitrd -o /boot/initrd.img-something-whatever something-whatever[/FONT][/INDENT]

---

