---
title: "[SOLVED] windows's time resets after ubuntu install. whats this??"
date: 2008-09-09
forum: General Help
---

### Post by SheikhAmanAlam on 2008-09-09
hi.
i have installed ubuntu on one of my hard drives, and my ubuntu's version is 8.04.1
after installing, i settled GRUB as my default boot loader and added windows's entry into its menu.lst to find windows's option every time i boot.
but after doing this, whenever i turn on windows, i get my time settled back on 12:00 am and i have to synchronize my clock with microsoft ime servers evertime.

why this is happening??
did grub do anythng with CMOS??
any fixes to this???

---

### Post by SheikhAmanAlam on 2008-09-09
does anyone know about this problem???

---

### Post by SheikhAmanAlam on 2008-10-29
Hellow??!!
anybody there??

---

### Post by SheikhAmanAlam on 2008-10-29
Hellow??!!
anybody there??

---

### Post by InFeh on 2008-10-29
Please don't spam. I think the cause of this is that Ubuntu sets the system clock after synchronizing with an NTP server when ntpd starts.

Try booting Windows twice without booting Ubuntu in between. Does it still happen?

If not, try disabling your time synchronization in Ubuntu.

---

### Post by SheikhAmanAlam on 2008-10-29
> **InFeh said:**
> Please don't spam. I think the cause of this is that Ubuntu sets the system clock after synchronizing with an NTP server when ntpd starts.

Try booting Windows twice without booting Ubuntu in between. Does it still happen?

If not, try disabling your time synchronization in Ubuntu.
well sorry, i wasnt spamming, there might have been some problem with either my browser or internet connection which made the reply get posted twice.

how to disable the time sync in ubuntu??

why would it be creating a problem?
i had selected correct location at the time of install so whichever server ubuntu syncs my time with, should give me the correct time, i.e. GMT +5:30

---

### Post by _sAm_ on 2008-10-29
> **SheikhAmanAlam said:**
> hi.
i have installed ubuntu on one of my hard drives, and my ubuntu's version is 8.04.1
after installing, i settled GRUB as my default boot loader and added windows's entry into its menu.lst to find windows's option every time i boot.
but after doing this, whenever i turn on windows, i get my time settled back on 12:00 am and i have to synchronize my clock with microsoft ime servers evertime.

why this is happening??
did grub do anythng with CMOS??
any fixes to this???
Open a terminal and run:
```
sudo gedit /etc/default/rcS
```
Enter your password when asked. 
Change **UTC=yes** to **UTC=no**
Press save and close gedit. You will need to set the correct clock in Windows once next time you boot it.

> why this is happening??
Read here to learn why; [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by SheikhAmanAlam on 2008-10-29
Thanks a lot sam fro all the info.
cant i make windows use UTC time???
bcz the article u just directed me to, says that its always goodto store time in UTC format.
what say?

---

### Post by _sAm_ on 2008-10-29
> cant i make windows use UTC time???
No, only Linux support this. So for dualboot you need to change it as explained before, or the time will be wrong on Windows.

---

### Post by SheikhAmanAlam on 2008-11-04
whoosh
that worked.
thanks a lot.
problem solved!!

---

