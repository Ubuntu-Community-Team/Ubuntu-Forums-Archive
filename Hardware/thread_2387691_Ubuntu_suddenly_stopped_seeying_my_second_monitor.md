---
title: "Ubuntu suddenly stopped seeying my second monitor"
date: 2018-03-22
forum: Hardware
---

### Post by andrey16 on 2018-03-22
*sign*
So, this is another iteration of my struggles with Ubuntu.
I hope there is some light at the end of the tunner and it's not an incoming train.

Since the last time of me unable to  solve Nvidia drivers issues I reinstalled Ubuntu once again.
Did software updates and disabled automatic ones.
Three weeks everything was file.

Until at some point I've started PC without external power (not the first time, but just in case it matters).
The screen was at minimum brightness and no brightness controls via UI or Fn-F11, Fn-F12 worked (I wasn't able to  find the UI brightness config at all actually).
External monitor is not detected. I restarted to Windows (don't kill me for that!) to make sure that external monitor is detected and works as usual.
Touchpad settings disappeared from  Settings => Devices => Mouse and touchpad.

Machine: Dell XPS 15 9650 (2017), 16GB Ram, dual video card (integrated Intel + Nvidia 1050).


`grep EE  /var/log/Xorg.0.log`
[     4.869] (EE) open /dev/dri/card0: No such file or directory
[     4.869] (EE) open /dev/dri/card0: No such file or directory
[     4.869] (EE) Screen 0 deleted because of no matching config section.
[     4.874] (EE) AIGLX: reverting to software rendering

`lpcpi`: [https://pastebin.com/ytE7RAnK](https://pastebin.com/ytE7RAnK)


What I've tried so far: install and use nvidia-384 drivers. However, my machine restarts on boot just like previously.
There is no /etc/X11/xorg.conf file contrary to time before last Ubuntu reinstall.
output of `lspci`: [https://pastebin.com/ytE7RAnK](https://pastebin.com/ytE7RAnK)
output of `lshw -C display`: [https://pastebin.com/164fZ1h1](https://pastebin.com/164fZ1h1)

Also, my machine hangs on reboot, tried `acpi=off`, `noacpi`, `nomodetset`. So I have to hard switch off every time I want to restart.
And, as I'm tying this, looks like  my machine is running much slower then usual, 
```
 1813 andrew    20   0 3097852 377416  94124 R 26,2  2,3   8:00.51 gnome-shell                                       
 3097 andrew    20   0 1495996 439052  74220 S 17,9  2,7   0:18.12 chrome                                            
 4063 andrew    20   0 1590520 438744 124724 S 16,9  2,7   3:01.12 chrome                                            
 1601 root      20   0  547624 133268  38604 S  8,3  0,8   3:02.20 Xorg         
```

Guys, I'm on edge of despair, like erasing this OS and never  using it again. Please lend me a hand in this one :(

---

