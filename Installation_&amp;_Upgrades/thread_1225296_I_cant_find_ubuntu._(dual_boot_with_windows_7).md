---
title: "I cant find ubuntu. (dual boot with windows 7)"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by litechocolate on 2009-07-28
After I installed the windows 7 beta yesterday I noticed that I could no longer find ubuntu. I know the operating system is still intact because I partitioned my hard drive. 54 gb for ubuntu and 54 gb for windows 7. How do I switch back to ubuntu without having to do clean install?

---

### Post by x22 on 2009-07-28
I found this worked OK--

[http://www.andrejciho.com/linux/repairing-grub/](http://www.andrejciho.com/linux/repairing-grub/)

---

### Post by merlinus on 2009-07-28
Boot from live cd, open a terminal and enter these commands:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

Then restart.

---

