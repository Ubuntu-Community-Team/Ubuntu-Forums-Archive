---
title: "Frustrated.UBuntu Automatically logs out.."
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by xthaparian on 2007-06-20
Hi
I was so much determined to 100% switch to Ubuntu this time..but looks like I have to go back to windows..

I had a perfect setup of Ubuntu with everything running on it, but i face a very very peculiar problem.

I used ATI X850XT AGP. 
At the GDM when i log in. The screen logs in..and then looks like it crashed..it kicks me out back to GDM?
I tried failsafe GNOME and still same..crashes and kicks me out back onto GDM..

I tried restricted driver and still the same...

Its driving me nuts..
Please help me Geeks..of Linux.

---

### Post by ukripper on 2007-06-20
Reboot your machine and go into recovery mode and reconfigure xserver-xorg.

EDIT:

Did it happened after instaling new theme? If yes then go to gdm.conf and amend it to theme=HUMAN

---

### Post by xthaparian on 2007-06-20
OK
So what command should i use to reconfigure ?

---

### Post by ukripper on 2007-06-20
```
sudo dpkg -reconfigure xserver-xorg
```

and if you wanna give gdm.conf a try then you have to do it using vi editor which is command line based if you cant use gedit. for that :
```
sudo vim /etc/gdm/gdm.conf
```

first try reconfiguring your xserver-xorg

---

