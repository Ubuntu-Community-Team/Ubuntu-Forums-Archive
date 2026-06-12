---
title: "Black screen when connecting via VGA to TV"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Jeinhor on 2009-06-30
Hello,

I installed Ubuntu Server 9.04 Jaunty, configured RAID and then installed Gnome using:

```
sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
```

Everything worked fine on my 17" LCD display. Since this was meant to be a HTPC, I then moved it to the TV and connected it via VGA. The problem: when Ubuntu tries to boot into Gnome, the screen gets black, nothing happens. Things I have tried:

1) Installing Ubuntu Desktop
2) Install other graphic drivers (though it shouldn't be the problem since it is working correctly with one display)
3) Hardcoded the resoltion 1024x768 (as the TV is using)
4) Installed everything connected at the TV from step 0

Anyone know why this happens? The same hardware ran a Windows-based HTPC before, working fine.

Thanks in advance!

---

### Post by Jeinhor on 2009-07-01
Maybe should add, the TV is a Panasonic 42PX80 and has a native resolution 1024x768. I don't know about refresh rates and such, maybe that's the problem?

---

### Post by Jeinhor on 2009-07-01
Aww, comon guys, I know the sun is shining outside, but that's no excuse! ;-)

Will have to go back to Windows otherwise =(

---

### Post by Jeinhor on 2009-07-06
Solved in this thread: [http://www.linuxquestions.org/questions/ubuntu-63/black-screen-works-on-vga-to-monitor-but-not-on-vga-to-tv-737165/?posted=1#post3598023](http://www.linuxquestions.org/questions/ubuntu-63/black-screen-works-on-vga-to-monitor-but-not-on-vga-to-tv-737165/?posted=1#post3598023)

---

