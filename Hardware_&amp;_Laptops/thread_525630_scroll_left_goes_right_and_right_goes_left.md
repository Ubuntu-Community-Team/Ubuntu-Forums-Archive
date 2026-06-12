---
title: "scroll left goes right and right goes left"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by adam_r on 2007-08-14
hello, 
i got a logitech vx revolution mouse. i got it working with evdev.. but my left scoll goes right and right goes left, i tried changing to 7 6 instead of 6 7 in xorg.conf .. and i tried pointer = 1 2 3 4 5 7 6 8 9 10 11 in .Xmodmaps and it didnt work, does anyone have a solution?

---

### Post by Parksy on 2007-08-16
I think the correct filename is .Xmodmap.  You also need to make sure that it loads at boot; I've read that these commands will do the trick:
```
gconftool-2 --list-type string --type list --set /desktop/gnome/peripherals/keyboard/general/known_file_list "[.Xmodmap]"
gconftool-2 --list-type string --type list --set /desktop/gnome/peripherals/keyboard/general/update_handlers "[.Xmodmap]"
```

---

### Post by adam_r on 2007-08-16
naa, .Xmodmaps was allready loaded:

```
adam@adam-laptop:~$ xmodmap -pp
There are 12 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
[COLOR="Red"][B]        6              7
        7              6[/B][/COLOR]
        8              8
        9              9
       10             10
       11             11
       12             12
```

and still no change... i'm using "evdev" as the mouse module for xorg.conf.. mybe it's because of that?

---

### Post by Parksy on 2007-08-16
I'm using evdev for my MX Revolution.'  Here are my settings:

xorg.conf:
```
Option          "ZAxisMapping"          "4 5 6 7"
```

.Xmodmap
```
pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16
```

And the side scrolling works as expected.

---

