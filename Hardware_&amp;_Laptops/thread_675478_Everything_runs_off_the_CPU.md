---
title: "Everything runs off the CPU??"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by slayer04 on 2008-01-22
I have my video card divers installed and running, yet every program and process runs directly off the CPU nothing is put on the ram or video card. I have know idea on whats causing it so any help would be appreciated.



2.8 Pentium 4, 1650 ATI pro, 1.5 GB ram, 80GB and 160GB hard drive, and dual boot with win XP

---

### Post by Yellow Pasque on 2008-01-22
Huh? Of course your computer is using RAM. What's the output of:
```
free -m
```

---

### Post by slayer04 on 2008-01-22
ok I used free -m and it told me that its using only 517 MB but when I see how much in the system monitor it displays a solid 0, while the CPU jumps around always remaining above 40%

---

### Post by Yellow Pasque on 2008-01-22
What processes are consuming that much CPU?

---

### Post by slayer04 on 2008-01-23
python and xgl between the 2 they take 30% and when I open a program no matter what it is it will take up  the rest of the CPU

should  XGL be running off my video card and not my CPU?

and the totem player runs off the CPU too but shouldn't that be mostly on the video card so it doesn't take up so much CPU?

---

### Post by Yellow Pasque on 2008-01-23
XGL is going to use some video card  resources and some CPU resources. ATI's driver isn't the best, and the XGL backend isn't the best either.

Here are your options:
1. Live with what you have
2. Uninstall XGL & compiz to lower CPU usage
3. If your X1650 is PCIe, you can try the latest Catalyst drivers. Be sure to uninstall XGL first

---

### Post by slayer04 on 2008-01-23
what should I do about programs jumping the CPU, should open office and gimp really take 70%  ?

---

