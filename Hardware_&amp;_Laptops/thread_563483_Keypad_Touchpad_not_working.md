---
title: "Keypad Touchpad not working"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by mohit.srivastava on 2007-09-30
Hi,
I have a lenove laptop 7761-6AQ and a major problem i am having with using Ubuntu 7.0.4 is that it is not detecting my touchpad and keypad. So each time i boot into Ubuntu i have to attach an external USB keyboard and mouse to work into Ubuntu. Is this some Ubuntu issue or mayb is it the laptop compatibility problem.

Does anyone have any suggestion as to what should be done???....:confused::confused:

---

### Post by eggdeng on 2007-09-30
Just a shot in the dark but it could possibly be a graphics related issue. Which graphics driver are you using? You could try reverting to the vesa driver to see if it persists.

---

### Post by mohit.srivastava on 2007-09-30
Hi,
Well i am using the nvidia graphics driver for ubuntu. Also tht i am having 2 OS's - Windows and Ubuntu and both the touchpad and keypad work fine in Windows.

Any advices??...:confused:

---

### Post by eggdeng on 2007-09-30
If you want to check whether the problem is caused by the graphics driver, back up your xorg configuration file```
 sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.conf.bkp
``` Open the original file ```
sudo gedit /etc/X11/xorg.conf
``` & replace the string "nvidia" with "nv". Logout and login again. If you have problems logging back in to a graphical environment, just type ```
 sudo mv /etc/X11/xorg.conf.bkp   /etc/X11/xorg.conf
``` to restore the backed up file.

---

### Post by mohit.srivastava on 2007-10-02
hiii,
I tried that also but it did not work....any other suggestions???

---

