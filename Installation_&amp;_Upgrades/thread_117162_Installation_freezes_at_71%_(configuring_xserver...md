---
title: "Installation freezes at 71% (configuring xserver......)"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by duckman148 on 2006-01-14
I am able to use the live cd just fine (ver. 5.10), but when I try installing Ubuntu, it freezes at 71 % during the 2nd phase of installation at "configuring xserver-.....". 

I really am looking forward to using & learning more about Linux, but this is frustrating for a newbie to Linux. This is the 2nd cd I have burned. I may try burning at a lower speed, but the live cd works just fine.....

The error screen comes up and says that I could try reinstalling the package or a slightly different one, but I am not sure how to do that. Ihave tried installing from scratch twice now, and it fails at the same place each time.

- I am not new to computers, just new to Linux....

Thanks for your help.

---

### Post by Sp@z on 2006-01-14
I highly reccommend checking the Md5 to make sure the cd is good and also I burned mine at the slowest speed possible it took a while but I have a good CD while waiting for the ones in the mail. It is definatly frsutrating but well worth the headache..........

---

### Post by duckman148 on 2006-01-14
Thanks I was actuall able to load xserver from the command line, but now I have a bit of a new problem. My screen resolution is only 800 x 600 at the highest...

---

### Post by Mustard on 2006-01-14
Try running this command in terminal...

```
sudo dpkg-reconfigure xserver-xorg
```

Just give the default answers for anything you don't know the answer to.  Eventually you should get to an option to set the various resolutions you want.  Add the resolutions you know are supported and then continue to then end and it will reconfigure your /etc/X11/xorg.conf file (which handles all this type of stuff).

---

