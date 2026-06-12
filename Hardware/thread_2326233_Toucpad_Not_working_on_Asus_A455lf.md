---
title: "Toucpad Not working on Asus A455lf"
date: 2016-05-29
forum: Hardware
---

### Post by chrisman2 on 2016-05-29
i'm finishing installing ubuntu i try install packet what i need like driver VGA and APPs 
but after i try suspend, Toucpad not working properly please helpme how to fix it?

---

### Post by courtney2 on 2016-06-04
I was helping a friend pick a laptop for Linux a while back, and found Asus can be very hit and miss with hardware support. I found that for some of their models, they use their own proprietary touchpad driver (stupid huh?). Go to a terminal and type the command "xinput list" and output what you get.

---

### Post by chrisman2 on 2016-06-22
ini gan


```
chrisman@Geretsunova:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                       id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
chrisman@Geretsunova:~$
```*EDITED by DuckHook*
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by DuckHook on 2016-06-22
*Thread moved to **Hardware** as the more appropriate forum.*

---

