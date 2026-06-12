---
title: "Assign key combination to a particular script to get keyboard backlight keys working"
date: 2013-08-06
forum: Hardware
---

### Post by bacchusmarsh on 2013-08-06
I have a Samsung np700z5a and have managed to get most features working but would love to get the keyboard backlight keys working.
The keyboard is backlight but I cannot adjust the brightness, though when it is very sunny the auto sensor seems to turn them off.

I have tried several methods including through the terminal. I have discovered that this works through the terminal:

     echo 6 > /sys/class/leds/samsung\:\:kbd_backlight/brightness

after an

    sudo su

(but not, 

sudo echo 6 > /sys/class/leds/samsung\:\:kbd_backlight/brightness where i get permissions denied).

I have tried running this in AutoKey as this script:

    #!/bin/bash
    sudo su
    echo 3 > /sys/class/leds/samsung\:\:kbd_backlight/brightness

and assigned it to some keys in AutoKey but it did not work.

i noticed that when i tried to assign it to the Fn + F9 key, this key and FN + F10 where not recognised at all (these are the keys designated to turn the keyboard backlight up and down in a windows install) so I assigned it to SUPER + - instead. as i said it does not work.

I have tried several other methods, following several threads but nothing seems to work for me

---

### Post by bacchusmarsh on 2013-08-07
All I want to do is assign:
sudo su
echo 6 > /sys/class/leds/samsung\:\:kbd_backlight/brightness

to a keyboard shortcut. Preferably with out having to enter my password everytime, but at this point I will take anything.

I know this sort of thing has been written about a lot but I cannot get it to work.

Any help?

---

