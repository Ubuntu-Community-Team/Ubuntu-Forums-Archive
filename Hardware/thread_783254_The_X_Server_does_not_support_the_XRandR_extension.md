---
title: "The X Server does not support the XRandR extension"
date: 2008-05-05
forum: Hardware
---

### Post by xodroolis on 2008-05-05
Until recently i was using Ubuntu 7.10.
The graphics were fast.
Days ago I did an upgrade to Ubuntu 8.04.
Since then:
I can still use 3d environment effects, but the screensaver for example runs extremely slow
By trying to set the screen resolution, i get this massage
"The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available."
I use Ati radeon 9600 and i was using the Ati radeon non free driver.
Any help?

---

### Post by gajanan.khandake on 2009-08-11
I am having same problem as "xodroolis" is having. 
My system details are-
Intel D101GCC mother board with ATI Radon Xpress 200 series on board graphics card.

Previously, i.e. when i was using Ubuntu gutsy i was able to change the resolution but recently, when i upgraded to hardy i am getting error on selecting the "Screen Resolution" menu option. The Error state that "The X Server does not support the XRandR extension".

Dose any one knows how to solve this problem?

---

### Post by gajanan.khandake on 2009-08-11
Hello xodroolis,
    I think that i have solved our problem.

I applied following steps after opening up terminal & in home folder.

1) Create a xserver-xgl directory in .config folder. 
```
gajanan@khandake:~$ mkdir .config/xserver-xgl/
```

2) Move to just created xserver-xgl folder. 
```
gajanan@khandake:~$ cd .config/xserver-xgl/
```

3) Create a file named disable
```
gajanan@khandake:~/.config/xserver-xgl$ touch disable
```

4) Check that file is correctly created.
```
gajanan@khandake:~/.config/xserver-xgl$ ls -l
total 0
-rw-r--r-- 1 gajanan gajanan 0 2009-08-11 14:29 disable
gajanan@khandake:~/.config/xserver-xgl$
``` 

5) Then restart x-server by pressing
```
Ctrl+Alt+Backspace
```

6) Log into the system and Check out 
```
System->Preferences->Screen Resolution
``` 

and it is working now. :P

Thanks to PeterPall Soultion #24 at launchpad.net with [[COLOR="Blue"]Bug #199359[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/199359"), no more "The X Server does not support the XRandR extension" for me. 

xodroolis or any one who is applying this solution please confirm it here if if worked with you

Thank you!

---

### Post by majickmann on 2011-11-22
Worked for me on RHEL5.7...
:-)

---

