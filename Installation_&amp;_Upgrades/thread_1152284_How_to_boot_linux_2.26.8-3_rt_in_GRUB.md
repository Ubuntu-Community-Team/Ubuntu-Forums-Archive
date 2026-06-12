---
title: "How to boot linux 2.26.8-3 rt in GRUB"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-05-07
I just used synaptic to install Ubuntu Studio and all the packages that come with it, and I was wondering how to use GRUB to boot the kernel that comes with it.
I have tried using the commands in the GRUB command line for the Ubuntu Studio linux kernel, but it didn't start usplash and it looked like it was starting recovery mode.

---

### Post by zvacet on 2009-05-07
Edit grub menu list 

```
gksudo gedit /boot/grub/menu.lst
```

and find your kernel and line 

root=UUID=xxxxxxxxxxxxxxxxxxxxxxx ro quiet splash 

**quiet** is what you need to get splash

---

### Post by camper365 on 2009-05-08
Out of curiosity, what does the rt kernel do?
I know rt stands for real-time, but what gets put in real-time?

---

### Post by logos34 on 2009-05-08
here's the -rt wiki page [explanation]("http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_real-time.3F")

---

### Post by camper365 on 2009-05-08
I understand what real-time is, but which program specifically get put in real-time when run under this kernel?

---

