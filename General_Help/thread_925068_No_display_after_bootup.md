---
title: "No display after bootup"
date: 2008-09-20
forum: General Help
---

### Post by Dr.Gee on 2008-09-20
I am a newb who just installed Ub 8.0.

I get display on bootup(UB splash screen with progress bar)but after that nothing on the screen. I know the OS is working because I get sounds when keys are depressed.

Help.:-k

---

### Post by sayakb on 2008-09-20
Press Ctrl+Alt+F1 and type in your username and password. Then try these two commands:
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```
Reboot once and see if it works now.

---

### Post by Dr.Gee on 2008-09-20
No luck. Says startx isnt installed

---

### Post by Nepherte on 2008-09-20
replace startx with:
```
sudo /etc/init.d/gdm start
```

---

### Post by Dr.Gee on 2008-09-20
> **Nepherte said:**
> replace startx with:
```
sudo /etc/init.d/gdm start
```

Thanks,but it says that is not installed either

---

### Post by sayakb on 2008-09-20
Is it the server ISO or the barebone ISO that you downloaded? If so, it does not have a GUI. You have to do, for gnome:
```
sudo apt-get install ubuntu-desktop
```
KDE:
```
sudo apt-get install kubuntu-desktop
```
KDE4:
```
sudo apt-get install kubuntu-kde4-desktop
```
XFCE:
```
sudo apt-get install xubuntu-desktop
```
and so on..
After you install any of these, you have to reboot and the login manager (gdm, kdm, xdm etc.) would start.

---

### Post by Dr.Gee on 2008-09-20
It is the alternative cd ubuntu version 8 non server version.

I run that command and it says:desktop is already the newest version.:confused:

---

