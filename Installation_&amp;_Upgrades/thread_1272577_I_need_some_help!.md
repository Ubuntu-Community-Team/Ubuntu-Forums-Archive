---
title: "I need some help!"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by zking on 2009-09-22
I set up a dual-boot with Vista and Ubuntu on my computer. 

When I restart my computer, it gives me options, to boot into Vista, or boot into Ubuntu. 

Ubuntu seems like the primary O.S. If I don't do anything within 10 seconds on the boot menu, it automatically starts up Ubuntu. 

I don't want this. I want Vista to be the primary O.S, and I want my computer to boot into Vista automatically within 10 seconds on the boot menu if I don't do anything, instead of Ubuntu. 

Can I do this? How? 

Thanks,

---

### Post by oldos2er on 2009-09-22
Install the package **startupmanager** which will allow you to choose a default OS, among other things.

---

### Post by snowpine on 2009-09-22
Or, edit your menu.lst file:

```
gksu gedit /boot/grub/menu.lst
```

Look for the line that says something like:

```
default 0
```

Change the number to whichever row Vista appears at on the menu, starting your counting from 0. In other words, if Vista is the 4th item on your grub menu:

```
default 3
```

Save the changes and reboot.

---

### Post by zking on 2009-09-22
> **snowpine said:**
> Or, edit your menu.lst file:

```
gksu gedit /boot/grub/menu.lst
```Look for the line that says something like:

```
default 0
```Change the number to whichever row Vista appears at on the menu, starting your counting from 0. In other words, if Vista is the 4th item on your grub menu:

```
default 3
```Save the changes and reboot.

This worked perfectly. Thanks! :)

---

### Post by presence1960 on 2009-09-22
> **zking said:**
> This worked perfectly. Thanks! :)

Just be aware that when you upgrade Ubuntu's kernel you are going to have to edit that default # in menu.lst as Vista will move further down in the order as the new kernels are placed up top.

---

