---
title: "External drive"
date: 2018-02-27
forum: Hardware
---

### Post by b1jqxk44 on 2018-02-27
One of my external drives, which I've been putting files on for over a year. Is now read only? How does it change from read, write and execute to read only and I've done nothing out of the ordinary. I need to know how to change it back to rwx.

---

### Post by HiRez_L on 2018-02-27
Did you try remounting as rw? Like so:
```
 [COLOR=#111111][FONT=Consolas]sudo mount -o remount,rw {/partition/identifier} {/mount/point} [/FONT][/COLOR]
```[COLOR=#111111][FONT=Consolas]

So, say for example my / filesystem came up as read only, and it was on /dev/sda1, I could remount it rw by issuing

[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]sudo mount -o remount,rw /dev/sda1 / [/FONT][/COLOR]
```

---

### Post by slickymaster on 2018-02-27
Thread moved to **Hardware** for a better fit

---

### Post by mastablasta on 2018-02-27
> **b1jqxk44 said:**
> One of my external drives, which I've been putting files on for over a year. Is now read only? How does it change from read, write and execute to read only and I've done nothing out of the ordinary. I need to know how to change it back to rwx.

if drive goes bad it will move to read only to protect the data. backup the data from it before messing with it.

---

### Post by b1jqxk44 on 2018-02-27
That worked great. Thank you.

---

### Post by b1jqxk44 on 2018-02-27
It went back to read only again. So I'm off to go buy a drive and transfer all the files before I lose them.

---

