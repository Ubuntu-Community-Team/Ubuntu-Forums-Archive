---
title: "ubuntu won't remember my resolution"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by fekimoki on 2005-08-01
in adition to my monitor problem in [http://www.ubuntuforums.org/showthread.php?t=53509](http://www.ubuntuforums.org/showthread.php?t=53509)
my ubuntu also won't remember my resolution, so i have to make it to 1152*864 everytime i logged in.
iv read wiki about screen res.. still no clue..
help! thx

---

### Post by Xian on 2005-08-01
How exactly are you setting the resolution?

You really should do it using the command below,
or just hand edit your /etc/X11/xorg.conf file.

```
$ sudo dpkg-reconfigure xserver-xorg
```

---

