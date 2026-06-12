---
title: "[SOLVED] PS/2 to USB dongle"
date: 2008-07-10
forum: General Help
---

### Post by tad1073 on 2008-07-10
I have a ps/2 to usb dongle that I want to use to hook my usb mouse to, but when I hook it up the mouse doesn't work. Any suggestions?

---

### Post by PmDematagoda on 2008-07-10
I don't think that the mouse and various other input devices have been made hot-pluggable on the version of X currently on Ubuntu 8.04, so you may have to reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
or boot Ubuntu in Recovery Mode and select Xfix and then see if the mouse is now detected and working.

---

### Post by tad1073 on 2008-07-10
> **PmDematagoda said:**
> I don't think that the mouse and various other input devices have been made hot-pluggable on the version of X currently on Ubuntu 8.04, so you may have to reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
or boot Ubuntu in Recovery Mode and select Xfix and then see if the mouse is now detected and working.

Will try it tommorow, the dongle is in my desk drawer at work.

---

### Post by tad1073 on 2008-07-12
> **PmDematagoda said:**
> I don't think that the mouse and various other input devices have been made hot-pluggable on the version of X currently on Ubuntu 8.04, so you may have to reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
or boot Ubuntu in Recovery Mode and select Xfix and then see if the mouse is now detected and working.

I tried both of your options but I get errors. I started a thread about it [HERE](http://ubuntuforums.org/showthread.php?t=857258)

---

