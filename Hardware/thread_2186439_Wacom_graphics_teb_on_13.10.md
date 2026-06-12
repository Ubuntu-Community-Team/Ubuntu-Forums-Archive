---
title: "Wacom graphics teb on 13.10"
date: 2013-11-07
forum: Hardware
---

### Post by g-marriner on 2013-11-07
Hi,

I have just purchased a Wacom intuos 4 PTK1240 and want to  use it on a laptop running Ubuntu 13.10. After plug in, the mouse moves  on the screen but none of the buttons work. I also purchased Pen to use  with it and this isn't working at all! I am new to Ubuntu and Wacom so  am struggling alot! Any help would be fantastic,

G

---

### Post by Favux on 2013-11-07
Hi G,

Welcome to Ubuntu forums!


An Intuos 4 should just be plug and play on Saucy (13.10) so something isn't right.  At a guess the tablet is on the evdev X driver and not the Wacom X driver.

What is the output of the following commands in a terminal?
```
xinput list
```
and
```
lsmod | grep wacom
```

---

### Post by g-marriner on 2013-11-19
Hi favux, thanks for your reply, here is the info

gary@Gary-Eurofarm:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=13    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 12x19 stylus                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 12x19 eraser                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 12x19 cursor                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 12x19 pad                     id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=12    [slave  keyboard (3)]
gary@Gary-Eurofarm:~$ lsmod | grep wacom
wacom                  57412  0

---

### Post by Favux on 2013-11-19
According to xinput list the tablet is on the Wacom X driver because stylus, eraser, cursor, and pad are appended to the parent device name "Wacom Intuos4 12x19".  And you can prove that by running **xsetwacom list** in a terminal and getting the same 4 daughter devices.

Additionally from **lsmod** command the Wacom kernel module/driver is auto-loading.

So the tablet should be working.  When you say the pointer moves is that to a stylus?  Just not the one you bought?

Buttons can be configured through the Gnome Wacom applet in System Settings or using the KDE Wacom applet if you are using Kubuntu instead of Ubuntu Unity.  And you can always use xsetwacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

Tablets only support certain styli.  Are you sure you bought a stylus that works with your Intuos4?  Does it work with the tablet in Windows or OSX?

---

