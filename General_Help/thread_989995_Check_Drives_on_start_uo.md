---
title: "Check Drives on start uo"
date: 2008-11-22
forum: General Help
---

### Post by capo1949 on 2008-11-22
Hi All
I run 804 on a dell desktop, single boot
I am  'cheezed off' with the check disc operating afetr 30 boots or so, as I boot up my system 4/5 times a day this operation is a pain in the butt.

Can someone please advise how to either delete this function or change it to 128 boots

Thanks in anticipation
Graham

---

### Post by beno1990 on 2008-11-22
[http://ubuntuforums.org/showthread.php?t=295262]("http://ubuntuforums.org/showthread.php?t=295262")

I think this might be what you're looking for. ;)

---

### Post by philinux on 2008-11-22
Using the terminal you can set the boot number to anything you like. I would suggest once a month. So 150 reboots say.

Look up man tune2fs for further settings.

```
Shows file state and boot number

sudo tune2fs -l /dev/sda1  (give info)

sudo tune2fs -c 50 /dev/sda1 (changes the routine check interval to 50)

sudo touch /forcefsck  (forces a check next reboot)
```

---

