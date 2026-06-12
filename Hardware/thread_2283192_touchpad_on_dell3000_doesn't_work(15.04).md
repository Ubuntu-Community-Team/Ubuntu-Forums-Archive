---
title: "touchpad on dell3000 doesn't work(15.04)"
date: 2015-06-19
forum: Hardware
---

### Post by alocin05 on 2015-06-19
good morning,
I have a dell inspiron 3000 14"....
I tried a lot of distro but 14.04 based(ubuntu, lubuntu or mint) or debian based have problem with graphic and network cards also!!
15.05 seems to work good...the only problem is the touchpad....it seems to be dead but it seems to be into the xinput list
any tips?
thanks.

```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; DLL06AB:00 06CB:78F1                        id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]


```

---

### Post by alocin05 on 2015-06-20
touchpad has been detected....but ```
xinput --test 14
``` do nothing!! 
I installed "GPointing" and I realized that lubuntu see 2 touchpad.....I tried combination
1 enabled 2 disabled......1 disabled 2 enabled....both enabled or both disabled.....but nothing!!

---

### Post by its-the-merovingian on 2015-07-05
Did you solve this yet?  I have just bought a new Inspiron 3551 and the touchpad on that doesn't work either.

---

### Post by glyndon on 2015-08-08
Same here. 
It's a machine sold by Dell with Ubuntu 14.04 pre-installed (So you'd think it'd be supported).
Upgrading to 15.04 and the trackpad is inert.
Sadly, Dell's support site doesn't even recognize 14.04 as a valid OS for the machine (using its service tag).

---

### Post by yogich246 on 2015-11-11
Get a bluetooth mouse. Seriously. My brand new Dell Inspiron has same issue. I pulled out my bluetooth mouse.

---

