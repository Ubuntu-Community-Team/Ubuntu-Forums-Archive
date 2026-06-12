---
title: "Asus u80v keyboard backlight"
date: 2009-12-19
forum: Hardware
---

### Post by Salleman on 2009-12-19
Here goes:

I've been using ubuntu as my primary OS for the last two years, and been very happy with it.

Recently i bought a new lappy, an Asus U80V. First thing i did was rid it of Vista, and install ubuntu. Unfortunately a lot of things didn't work very well. No suspend/hibernate, no digital audio output, no control of brightness e.t.c. So i turned to windows 7 RC for a while.
With the release of 9.10 I'm back, and a lot of things seem to work a lot better. 
But still there is no keyboard backlight...
I've done a lot of searching, but hasn't found any answers.
Can anyone help?

Thanks

---

### Post by Myster on 2009-12-21
Install new kernel 2.6.32.
You need to compile this kernel. Or use the lastest version of ubuntu lycid lynx which must have this kernel.

echo 2 | tee /sys/class/leds/asus\:\:kbd_backlight/brightness

0: turn off
1 to 3 Luminous intensity varies

I still search how to setup hotkeys keyboard.

source: [http://forum.ubuntu-fr.org/viewtopic.php?pid=3118523](http://forum.ubuntu-fr.org/viewtopic.php?pid=3118523)

---

### Post by FLOZz on 2010-10-28
There is now a package for the hotkey:
[https://launchpad.net/asus-keyboard-backlight](https://launchpad.net/asus-keyboard-backlight)

add this ppa : [https://launchpad.net/~flozz/+archive/flozz]("https://launchpad.net/%7Eflozz/+archive/flozz")
Update the pkg list and install "asus-kbd-backlight"

---

### Post by FrostEternal on 2012-11-13
I'm not sure how to install said package. I'm new to Ubuntu and I don't really know much. I've added the ppa to the software sources but I can't find asus-kdb-backlight anywhere. Thanks in advance :)

Ok so I've managed to install but now I can turn the light on but not off, It is suppost to have 3 levels of brightness and it only has the 2nd and 3rd.

---

