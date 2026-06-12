---
title: "Screen Resolution not being remembered between Updates"
date: 2008-11-07
forum: General Help
---

### Post by jamesr on 2008-11-07
Hi All,

I am have an unusual problem with Hardy Heron (8.04) on HP Pavillion 8756C. The screen Resolution is not being remembered. The monitor is capable of 1280 x 1024.  Until the last update I was able to to reset the resolution using ```
sudo dpkg-reconfigure xserver-xorg
``` and it would hold until updates of the linux kernel came out. Now I cannot get the above code to work. The system shares keyboard and monitor via a KVM switch and the other system running xubuntu 8.04 automatically finds a higher resolution of the screen or at least gives the options of all resolutions. The HP system gives only 800x600 and 640x480 so it means viewing the forum pages is almost impossible. 

I cannot find the specifactions of the Monitor TTX 1770 but I have windows.inf file see attached file which includes this information. I was hoping to manually edit the xserver-xorg file but I do not know how to interpretate the *.inf file. 

The other way was to replace the on-board video with a video card.

Best Wishes
Jim R

---

### Post by jamesr on 2008-11-09
Hi Folks,

Just a short update in that the problem is partially solved.

Tried adding a video card, did not solve the problem, although gave a clue to another problem in that the 810 driver, on-board video was not being activated.

Removed additional video card.

Tried ```
sudo displayconfig-gtk
``` The first time did not work no sync?
Reboot still no sync
Using Ctrl-Alt-Backspace  eventually got to a working screen
```
sudo dpkg-reconfigure xserver-xorg
```
Retried ```
sudo displayconfig-gtk
``` Ensured that the 810e driver was set-up and active but using a lower resolution than the screen is capable. 
But now my login screen is only displaying part of the screen almost like a virtual desktop but enough to see the login. Once the gui was running, I could set-up and change the screen resolution (System-Screen resolution) but I have noted that locations of the trash bin is not to the fullright see attached picture. I have also attached the updated xorg.conf file. 

If anybody has suggestions, they would be appreciated. Also I will post if I am successful in solving the problem in case anybody has a similar problem.

---

