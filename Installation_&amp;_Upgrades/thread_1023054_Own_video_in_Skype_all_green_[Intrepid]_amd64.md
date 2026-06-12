---
title: "Own video in Skype all green [Intrepid] amd64"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by UbuGianlu on 2008-12-27
i've found this thread on forum

[http://ubuntuforums.org/showthread.php?t=945803&page=2](http://ubuntuforums.org/showthread.php?t=945803&page=2)

[SOLVED] Own video in Skype all green [Intrepid]


but i didn't solve my trouble because i've a amd64 distro of intrepid

so, at the solution

you can replace the second instruction so become: 

```
sudo gedit /usr/local/bin/skype
```

and paste

```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
```

note: it's not ***lib*** but ***lib32***

then make it executable

```
sudo chmod a+x /usr/local/bin/skype
```


thanks to eldragon for [partial] solution of my problem :KS

---

