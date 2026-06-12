---
title: "how to set 1440x900 resolution at 75Hz refresh?"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Mr.Duck on 2007-08-22
Hi, I need to set my monitor to 1440x900 75Hz. I don't know how to do it i am scared i will break ubuntu. I use that setting under windows so i know the hardware supports it. Is there a step by step guide I can follow? I do not know how to back up and restore config files if it all goes wrong.

thank you for your help.

---

### Post by gashcrumb on 2007-08-22
You should be able to run to System/Preferences/Screen Resolution and set the resolution and refresh rate from the "Screen Resolution Preferences" applet.

---

### Post by Mr.Duck on 2007-08-22
sorry I did not make clear that was 1st place I tried but that resolution is not there, only goes up to 1280x1024. I think some sort of editing of configuration files is needed but I don't know what I am doing.

---

### Post by oofnik on 2007-08-22
Do you have an Intel inegrated chipset? There is a bug somewhere in the Intel driver I believe that causes it not to read all of the supported resolution modes. A tool called 915resolution exists which fixes this problem by 'hacking' one of the video BIOS modes that are read and changing them to whatever you want. Do a quick search on the forums and you should be able to find how to use it easily.

---

### Post by Mr.Duck on 2007-08-22
I am using a VIA epia mini ITX system. Chipset is CN700.

---

### Post by spier on 2007-08-22
Reboot in  recovery mode , then run the command

```
dpkg-reconfigure xserver-xorg
```

Following  the steps, select your video card, then the desired resolutions.  Not sure Via  is in the drivers list, though.

---

