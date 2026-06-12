---
title: "How to change the default boot OS"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by yosepht on 2009-01-26
I have a dual boot system with Ubuntu 8.10. I am hoping to get
zoneminder working soon but in the meantime I would like my
system to default boot XP. What do I need to do to Grub for that
to happen? Your help is greatly appreciated.:)

---

### Post by tommy1987 on 2009-01-26
Simply edit the file residing at:

/boot/grub/menu.lst

You can change the order of the Operating Systems here.

---

### Post by balaknair on 2009-01-26
To change the boot menu order, you need to edit a file named menu.lst.
To do this open a terminal(Applications menu> Accessories> Terminal) with the following commands2)

1) Back up the existing GRUB menu.lst
*sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup*

2) Open the menu.lst file in Gedit text editor with root privileges
*gksudo gedit /boot/grub/menu.lst*

3) Now find the following sections in the file
a)
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

```

b)
```

# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

(The actual lines in your menu.lst will be slightly different from mine of course.)

Cut the text you find in b) and paste it just above the beginning of a)

```
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

```

Save and exit the file. Now GRUB will show Windows at the top of the list as default.

---

### Post by yosepht on 2009-01-26
:) Thank you very much that is very helpful.

---

### Post by Hobgoblin on 2009-01-26
Or you can install Startup-manager for a GUI method of doing it.

---

