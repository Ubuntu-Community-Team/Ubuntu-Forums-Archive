---
title: "Can't get 1280x800 resolution to work on old video card"
date: 2008-09-23
forum: General Help
---

### Post by halo000 on 2008-09-23
Hey everyone, I'm new to UBUNTU...and I think its' GREAT!!

However my laptop is old...I have and ATI mobility radeon 9200 laptop card.  I can get compiz fusion to work but only on a crappy resolution 1024x780.  

I'm really new to linux but I managed to work through everything to get Compiz to work. But I can't seem to fix this issue of the black bars on the side after I change the resolution.

I looked on google and it did say modify the x something but I tried that but it wouldn't let me save the new code.  Can someone help?

thanks in advance! i'm a believer in Ubuntu but i just want to get the resolution fixed until i switch.  

I have a compaq x1000 laptop.

---

### Post by bwang on 2008-09-23
To edit xorg.conf, you need to be root:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by halo000 on 2008-09-24
When you mean in the root...do I type this stuff in the terminal?

---

### Post by conundrumx on 2008-09-25
In Unix like operating systems "root" is the super user account, equivalent in some ways to "Administrator" on Windows.  Many of the operating system's inner workings, and some things that users just shouldn't need to do require you to be a super user, or root.  Sudo (Super User DO) is the most common way for a computer's owner or systems administrator to gain root access, as it only gives root on the command immediately following.  

So, "sudo gedit /etc/X11/xorg.conf" will open the file xorg.conf in the directory /etc/X11/ using gedit (more commonly referred to as Text Editor in the Ubuntu menus) with root privileges.

Please note, being root is dangerous.  It's a loaded gun, and many people have had to reinstall because of typos or bad advice.

---

