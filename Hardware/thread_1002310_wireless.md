---
title: "wireless"
date: 2008-12-04
forum: Hardware
---

### Post by AB109 on 2008-12-04
Hi, 
I'm new to this forum I have a problem with my laptop I can't get wireless internet. I have try different things but it doesn't work. My computer is a toshiba  satellite M305D-S4830. Can someone tell me how to make it work.

All really appreciate it.


thanks

---

### Post by ibutho on 2008-12-04
Hi and welcome to the forum

In order to get more help, you need to let us know the chipset that the wireless card uses. You can find out this information by running Applications -> Accessories -> Terminal and entering the commands
```
sudo lspci | grep -i net
```
Also run the command 
```
lsusb
```
Post back the output.

---

### Post by AB109 on 2008-12-04
The code -i dosent work

---

### Post by falcon61102 on 2008-12-04
Try this one:
```
sudo lshw -C network
```

---

### Post by Primal-id on 2008-12-04
If you find your wireless driver is installed properly and still having problems i'd recommend installing wicd instead of the gnome network manager.

---

### Post by ibutho on 2008-12-05
> **AB109 said:**
> The code -i dosent work

You need to copy the first command as it is. Its not two separate commands.

---

