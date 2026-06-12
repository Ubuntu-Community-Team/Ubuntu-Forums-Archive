---
title: "Unable to mount drive"
date: 2008-11-01
forum: Hardware
---

### Post by ShoeSh1ne on 2008-11-01
While trying to install ndisgtk using:

```
sudo apt-cdrom add
```

And press enter after inserting CD, I get an unable to mount drive error.

Obviously I'm looking for a fix, but if there is a workaround to get ndisgtk installed so I can install my wireless card drivers then that would be fine.

I should add that I did this successfully using VMPlayer to test it, so I decided to to an install and now it won't work.

---

### Post by cariboo on 2008-11-01
Can you manually mount the cdrom? In a terminal type:

```
sudo mount /dev/scd0 /media/cdrom
```

Jim

---

### Post by ShoeSh1ne on 2008-11-01
Hi Jim

Using your suggestion, I get this error

> cant find /dev/scd0/media/cdrom in etc/fstab or etc/mtab

---

