---
title: "Compiz on my laptop-Intel video card"
date: 2008-07-10
forum: General Help
---

### Post by b0ne3ce on 2008-07-10
Guys, is there anyone knows how to run compiz on Intel video card..
thanks,,..:(

---

### Post by Locutus_of_Borg on 2008-07-11
oh hai

i run compiz on an Intel 945GM

Works wonderfully


what is going wrong with yours?

---

### Post by wfp on 2008-07-11
I have a 865g intel chipset and it works. Have you followed these directions.> [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_enable_Compiz_Fusion_in_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_enable_Compiz_Fusion_in_Ubuntu)

---

### Post by Tithis on 2008-07-11
I run Compiz fine on my laptop which uses an intel 950GMA. Hopefully you don't run into the problems with video and openGL like I did.

---

### Post by sayakb on 2008-07-11
1. See 3rd page of the FAQ in Desktop effects and Customization for installing Compiz 0.7.6 (post 24)
2. Remove xserver-xgl package if it is installed
3. At a terminal, do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
4. Open CCSM (compizconfig-settings-manager) and goto preferences, and press Restore to Defaults button.

---

### Post by b0ne3ce on 2008-07-11
thanks....i will follow this steps.

---

### Post by sayakb on 2008-07-11
Btw, after doing #3, do restart X by pressing Ctrl+Alt+Backspace

---

### Post by b0ne3ce on 2008-07-11
.. do i have to install any driver for my graphics card...
and what is a compatible software??..

---

### Post by sayakb on 2008-07-11
For intel cards, you don't need a driver. Btw, did the effects work with the LiveCD?

---

