---
title: "help formating an external hard drive"
date: 2008-06-23
forum: Hardware
---

### Post by jrranbrody on 2008-06-23
i have a wd 250 g hard drive that i want to format, but i dont know how to do it. i heard that i can do it via ternimal but it dont know what codes to enter can someone help me?

---

### Post by wormser on 2008-06-23
I would recommend using the GUI program Gparted.  It is easy to use.  

```
sudo apt-get install gparted
```
```
gksudo gparted
```

To select your external drive use the drop down in the upper right hand corner.

---

### Post by prshah on 2008-06-23
> **jrranbrody said:**
> i have a wd 250 g hard drive that i want to format, but i dont know how to do it. i heard that i can do it via ternimal but it dont know what codes to enter can someone help me?

You can do it easily using the gparted program (Gnome Partition Editor). you'll find it in System-Administration-Partition Editor. If it's not there, install it with ```
sudo apt-get install gparted
```

If you insist on doing it via the terminal, you have to use fdisk to create the partitions and mkfs to "format" them. Post back with the output of ```
sudo fdisk -l
``` (With your external drive connected) and the partition scheme you want for your external drive, for more detailed instructions.

---

### Post by jrranbrody on 2008-06-23
thanks to bot of you you helped me out a lot. hey prshah the one with the terminal didnt work or at least i could not do it with that code

---

### Post by wormser on 2008-06-24
> **jrranbrody said:**
> thanks to bot of you you helped me out a lot. hey prshah the one with the terminal didnt work or at least i could not do it with that code

No problem.  Click the star icon on the posts that help.  Also, mark the thread solved.  Directions in my signature.

---

