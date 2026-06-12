---
title: "Logitech USB headset messing with mouse"
date: 2013-04-24
forum: Hardware
---

### Post by macsym on 2013-04-24
Hello all,

my Logitech USB Headset H340 is messing up with the internal touchpad of my laptop. Everytime I plug it in, it takes the control of my left click (it maintains the left click down). 

Here is a few information:
- Ubuntu 12.04 LTS 64bit
- Kernel 3.5.0-27-generic
- Dell Vostro 3360
- xinput returns:
max@max-vostro-3360:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD               id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; Logitech Inc. Logitech USB Headset H340     id=15    [slave  keyboard (3)]

- I have the same bug even if I log on the other Kernels (3.2.0-39-generic, 3.5.0-23-generic, 3.5.0-25-generic, 3.5.0-26-generic)

Note that I have another partition with the exact same configuration (Ubuntu 12.04 64bit with Kernel 3.5.0-27-generic) and this one is working fine.

Does anybody know how I could fix this?

Thank you very much for any help

---

### Post by filwaitman on 2014-01-04
I am facing exactly the same issue. Do you know what is happening?

NOTE: I have Xubuntu and Ubuntu-gnome installed (both in 13.10). It does not work only in Xubuntu - works properly in Ubuntu-gnome. Weird.  =/

---

