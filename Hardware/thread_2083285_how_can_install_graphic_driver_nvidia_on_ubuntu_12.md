---
title: "how can install graphic driver nvidia on ubuntu 12.10"
date: 2012-11-12
forum: Hardware
---

### Post by yosefcpu on 2012-11-12
how can insttall graphic driver nvidia on ubuntu 12.10
200 series 
gts 250 
512MB DDR3
iam beginner lunix 
:(:(:(

---

### Post by Yellow Pasque on 2012-11-12
```
sudo apt-get install nvidia-current
```

---

### Post by yosefcpu on 2012-11-13
The card is not defined
and not found setting system

[[http://www12.0zz0.com/2012/11/14/03/798587225.png](http://www12.0zz0.com/2012/11/14/03/798587225.png)]("http://www.0zz0.com")

---

### Post by Yellow Pasque on 2012-11-14
Ubuntu's sysinfo program often fails to detect the graphics card. Unless you are having issues with the graphics, do not worry about that.

It would be better to look at /var/log/Xorg.0.log to diagnose problems.

---

### Post by jerome1232 on 2012-11-14
Once you are using nvidia's driver, use nvidia tools, open nvidia-settings (search for it in dash) and see if that has correct info.

edit: In case you haven't yet, press ctrl+alt+t and drag and drop Temujin's command into the terminal window that appears.

---

### Post by yosefcpu on 2012-11-14
sorry dont understand iam bigner on lunix 
step by step please

---

### Post by jerome1232 on 2012-11-14
Did you run the command posted by Temujin?

---

### Post by yosefcpu on 2012-11-15
(Image converteted to thumbnail)

---

### Post by jerome1232 on 2012-11-16
So you installed nvidia current, to get driver information look at nvidia-settings.

Press the super (windows) key, type nvidia you should see something called nvidia x server settings, open it, that will give you driver information.

---

