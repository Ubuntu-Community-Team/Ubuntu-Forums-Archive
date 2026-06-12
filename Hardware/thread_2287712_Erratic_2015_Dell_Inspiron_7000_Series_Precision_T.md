---
title: "Erratic 2015 Dell Inspiron 7000 Series Precision Trackpad"
date: 2015-07-21
forum: Hardware
---

### Post by patrickdeanmullen on 2015-07-21
Dear all, 

I am running Ubuntu 15.04 on a new 2015 Dell Inspiron 7000 Series (specifically 7548).  I am experiencing troublesome behavior from my trackpad.  It works perfect one minute but the next it is completely erratic and I must turn off the trackpad and use an external mouse for the computer to be functional.  I have tried several fixes but all have failed.  The fixes I have tried: 

[http://www.penguintutor.com/news/hardware/dell-trackpad-ubuntu](http://www.penguintutor.com/news/hardware/dell-trackpad-ubuntu)
[http://askubuntu.com/questions/583861/touchpad-not-working-in-ubuntu-14-04-on-dell-inspiron-15-7547](http://askubuntu.com/questions/583861/touchpad-not-working-in-ubuntu-14-04-on-dell-inspiron-15-7547)

It is worth noting that I experience the same behavior on Ubuntu 12.04, 14.04, and 14.10. 

If it helps in identifying a solution, here is the output to 

```
xinput
```

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Performance MX                     id=10    [slave  pointer  (2)]
&#9116;   &#8627; MSFT0001:00 06CB:75BD UNKNOWN               id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]



``` where Logitech Performance MX is my external mouse.  

I am not sure if there are certain gestures that spur the erratic behavior but it happens too frequently.  Any help would be greatly appreciated.  

Cheers!

---

### Post by ryukent on 2015-09-08
Did you ever find a solution to this problem? I still find using the 7000 series touchpad in ubuntu really hard. Especially it seems to pick up my hand while typing.

---

