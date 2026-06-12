---
title: "Gts 250 installation"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by pugtm on 2009-08-13
So i bought a gts 250 nvidia graphics card today and when reading the manual it says if you are running windows to remove all the old drivers. my question is this, can i simply pop in the card and use the current nvidia drivers i already have installed or do i need to remove them as well?
Using the latest build of ubuntu

---

### Post by khelben1979 on 2009-08-13
Made a quick look at nVidia.com for that card:

Linux Display Driver - x86

[URL="http://www.nvidia.com/object/linux_display_ia32_185.18.31.html"]Version: 185.18.31
Operating System: Linux x86
Release Date: July 31, 2009[/URL]

Is this the driver you're currently using? (if it is, you should be good to go.)

---

### Post by pugtm on 2009-08-13
how do i find out?
and if i don't how do i install it?

---

### Post by khelben1979 on 2009-08-13
You should look for a program called nVidia X Server Settings. It displays what version you have.

---

### Post by pugtm on 2009-08-13
ok so my drivers are old, i tried to install the new ones but it returned a message saying unable to open file.
how do i get it to update then?

---

### Post by khelben1979 on 2009-08-14
The file is a script and you use the sh command to open it. It is also recommended to run the command using sudo so you get super user priviligies (root).

```
sudo sh NVIDIA-Linux-x86-185.18.31-pkg1.run
```

You also need to terminate your X session in order for you to install the driver.

Use the top command to display your processes. Then kill off the GDM processes after you have logged out from your X server session (simply use the logout button on the menu bar).

Some driver versions are not compatible with the kernel version in the Linux distribution and I can't tell whether this is the case now or not, so you'll just haveto try it out.

I would recommend that you install the driver after you have installed the graphics card. You should have both working graphics and the possibility to enter a text console with the drivers which comes default with the Linux distribution.

---

