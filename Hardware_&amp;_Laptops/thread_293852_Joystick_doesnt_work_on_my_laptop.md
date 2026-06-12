---
title: "Joystick doesnt work on my laptop"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by mmbb80 on 2006-11-05
Hi all!

First, im brazilian, and i cant write in english as well as i can understand english... so sorry for my bad english :-)

I cant figure it out how to make my joystick work on my laptop... When i plug the joystick, i can see the /dev/input/js0 reference, so i think the joystick is being recognized. Plus, in my desktop i can use the joystick, both with windows and slackware. In my notebook, it doesnt work neither in windows nor in ubuntu. Im almost sure its a hradware problem, but id like to know with someone can help me to understand what is happening.

I installed the package joystick and tried to use jstest /dev/input/js0, and thats what shows up:

Driver version is 2.1.0.
Joystick (LuenKeung Co.,Ltd USB  Joystick) has 2 axes (X, X)
Segmentation fault

when i try to use the joystick (with jscal or in the plugin config of epsxe, for example), none of the buttons or the axes works.

looking in another places, i saw references to the modules hid and joydev. both (actually usb_hid and joydev) are loaded... I dont know where or what i should look for, so if anybody could help me, it would be really nice.

Mauricio

---

### Post by tagra123 on 2006-12-12
> **mmbb80 said:**
> Hi all!

First, im brazilian, and i cant write in english as well as i can understand english... so sorry for my bad english :-)

I cant figure it out how to make my joystick work on my laptop... When i plug the joystick, i can see the /dev/input/js0 reference, so i think the joystick is being recognized. Plus, in my desktop i can use the joystick, both with windows and slackware. In my notebook, it doesnt work neither in windows nor in ubuntu. Im almost sure its a hradware problem, but id like to know with someone can help me to understand what is happening.

I installed the package joystick and tried to use jstest /dev/input/js0, and thats what shows up:

Driver version is 2.1.0.
Joystick (LuenKeung Co.,Ltd USB  Joystick) has 2 axes (X, X)
Segmentation fault

when i try to use the joystick (with jscal or in the plugin config of epsxe, for example), none of the buttons or the axes works.

looking in another places, i saw references to the modules hid and joydev. both (actually usb_hid and joydev) are loaded... I dont know where or what i should look for, so if anybody could help me, it would be really nice.

Mauricio

Using the Menu: Applications-Accessories-Terminal

Type
```

sudo gedit /etc/udev/rules.d/60-symlinks.rules
```

Place the following at the bottom of the file:

```
# Create Joystick /dev/js0, /dev/js1, etc using symlink 
#(links /dev/input/jsX to /dev/jsX)
KERNEL=="js[0-9]*", SYMLINK+="%k"
```

save the file and exit.

On reboot the joystick can be found by the programs looking for /dev/js0 as well as /dev/input/js0

---

