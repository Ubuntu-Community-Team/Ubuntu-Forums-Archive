---
title: "/home read only sometimes"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by esrange on 2009-05-08
After upgrading from 8.10 to 9.04 yesterday I sometimes get an error saying that /home (wich is on a separate partition) is mounted read only when it just seconds before was mounted read-write and then some time later it is read-write again. I also got some problems earlier today with sudo, when running sudo in a terminal or xterm it hangs the terminal and when I exit the terminal and open a new one I still have a process running with sudo when i do ps aux | grep sudo

I liked 9.04 yesterday because it fixed some problems I had with 8.10, but now I don't know, I wan't to be able to work with my computer and /home is quite important.

---

### Post by cariboo on 2009-05-08
Could you post what the onwership and permissions of your home directory? Here's what mine looks like:

```
4 drwxr-xr-x 60 jim jim 4096 2009-05-08 09:18 jim
```

---

### Post by esrange on 2009-05-08
> **cariboo907 said:**
> Could you post what the onwership and permissions of your home directory? Here's what mine looks like:

```
4 drwxr-xr-x 60 jim jim 4096 2009-05-08 09:18 jim
```
```

drwxr-xr-x 138 jakob jakob 6096 2009-05-08 16:45 jakob

```

---

