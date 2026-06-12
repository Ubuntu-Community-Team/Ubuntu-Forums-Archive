---
title: "Display problem on my laptop"
date: 2010-01-01
forum: Hardware
---

### Post by zeroandone on 2010-01-01
I installed Ubuntu 9.10 on my Dell laptop and found I am having some strange display problem. When I go to System->Administration->System Monitor, the window is not displayed correctly. Please see the attached screen. 

BTW, it didn't happen in Ubunt 9.04.

Can someone help me solve this?

Thanks,

Jeffrey

---

### Post by zeroandone on 2010-01-04
Anyone please? System Monitor is very important to me.

Thanks a lot,

Jeffrey

---

### Post by USB_NL on 2010-01-04
system monitor is an app to monitor your system it has nothing to do with your display

---

### Post by USB_NL on 2010-01-04
weird picture my system monitor looks normal

;)

---

### Post by zeroandone on 2010-01-04
> **USB_NL said:**
> weird picture my system monitor looks normal

;)
I know it is weird, that is why I am asking for help.

---

### Post by USB_NL on 2010-01-04
maby you can make it work with reinstalling system monitor in ubuntu software center or use an alternative one

---

### Post by alwayshere on 2010-01-04
.

---

### Post by zeroandone on 2010-01-04
Reinstalling System Monitor didn't help. Could it be something wrong with my display driver?

---

### Post by USB_NL on 2010-01-04
> **zeroandone said:**
> Reinstalling System Monitor didn't help. Could it be something wrong with my display driver?
have you tried a different screen resolution?

---

### Post by zeroandone on 2010-01-04
Yes, and it didn't help either.

---

### Post by USB_NL on 2010-01-04
hi again

```
free -m
```

In the terminal shows memory

---

### Post by USB_NL on 2010-01-04
maby you can use this until you fixed it
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by zeroandone on 2010-01-04
Thanks. I installed Conky, but it didn't meet my needs.
It is very frustrating that it worked perfectly in 9.04, but not in 9.10.

---

### Post by zeroandone on 2010-01-05
OK, it seems that many people have the same problem. [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406)

---

### Post by USB_NL on 2010-01-05
there is a sysmonitor screenlet maby you like it better then conky
```
sudo apt-get install screenlets
```

---

### Post by zeroandone on 2010-01-05
I finally installed KDE System Monitor which works very well. Thanks for your help.

---

