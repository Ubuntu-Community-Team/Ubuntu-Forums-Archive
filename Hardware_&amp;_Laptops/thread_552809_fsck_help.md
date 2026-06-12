---
title: "fsck help"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by darkskye on 2007-09-17
Please help!!


I have feisty, the newest version.

tonight must have been the 24 time ive booted my laptop, because it ran a forced fsck auto-check.


the bad new is that in around the 20 percentish it completely freezes. every time. this means i cant boot onto my system or anything. can anyone help, or does anyone know a bypass? 


please and thank you
-chris

---

### Post by uzerzero on 2007-09-17
Use a LiveCD to boot into the desktop, then use terminal.```
sudo fsck -y /dev/hdx
```

where hdx is the name of your hard drive that mount or fdisk gives you.

And to increase the number of boots between checks, try```
sudo tune2fs -c 50 /dev/hdx
```

where once again hdx is the name of your harddrive.

If you can't/don't have a LiveCD, try hitting control-c a lot during the percentage process. I had this problem once before and did that a lot and eventually it went all the way through. Second time I had to use the LiveCD.

---

