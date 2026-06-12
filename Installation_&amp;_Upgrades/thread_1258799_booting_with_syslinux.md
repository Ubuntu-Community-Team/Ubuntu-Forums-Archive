---
title: "booting with syslinux"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by Jasuramme on 2009-09-05
Hello. I've spent a lot of time, trying to find an answer, but no success.  I'm trying to install Ubuntu from usb-stick. I want to load isolinux.cfg and use standart ubuntu install dialog. So, i'm using syslinux. I'm starting isolinux.cfg, but there's code like: include menu.cfg, but it should be /isolinux/menu.cfg. I've tried to use APPEND root=/isolinux/, but nothing changed. Is there a way to install Ubuntu from not root folder, using syslinux, and how can i change the path, syslinux loading files from?

---

### Post by dandnsmith on 2009-09-05
I'm not sure I understand: syslinux/isolinux are ways to boot things, not a way to install stuff. Depending on what the configuration file says, and what anything in any initramfs has, something(s) will run at start.

I've forgotten (old age taking its toll) what some of detail is, but had to work thru a number of examples of usb stick loads using unetbootin to extract detail, and even then (while fresh) didn't manage to get certain types of linux together on one stick and bootable.

---

### Post by Jasuramme on 2009-09-05
Sorry, i will explain. I'm trying to boot from usb stick and start installing ubuntu, via standart installer. I have files from ubuntu cd on my flash stick. Usually, ubuntu boot installer starts with isolinux, but i'm trying to start it with syslinux(of course it differs only in file systems), BUT. when i'm starting isolinux.cfg, it can't find some files, for example, menu.cfg. Because it's trying to find it in the /menu.cfg but it is situated there: /isolinux/menu.cfg. I saw meanings, thats the best way to solve the problem is to copy isolinux and casper folders to root flash stick folder and start syslinux. But i want to know is there another way to start install menu? maybe can i write something in the syslinux.cfg, and it will search in isolinux/menu.cfg when it's making include menu.cfg command? So, can i change the root folder, the syslinux is loading files from? I've installed syslinux from windows and tried syslinux.exe -d /isolinux/ f:, but no success. command APPEND root=isolinux didn't help. And i can't find answer in the syslinux page. I hope, you will help. Thanks.

---

### Post by dandnsmith on 2009-09-06
OK, I really did understand the nub of the matter, but wasn't entirely sure that you weren't a little adrift - you're obviously not.

I'll try to sort out any notes I made but, as I said, found that different installer systems expect different placements for which you may need to delve rather deeply. The menus do differ, but I've forgotten what the key points are (sometimes you find there are 3 lot's of menus and it takes experimentation to find which are invoked as a result of something built in to the original construction.

---

