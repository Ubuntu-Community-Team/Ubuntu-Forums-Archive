---
title: "asus f2hf backlight keeps turning off"
date: 2008-06-16
forum: Hardware
---

### Post by eidam655 on 2008-06-16
hello,

this weekend i could not connect my laptop to any external monitor/tv. so i tried and reconfigured the X server (with dkpg-reconfigure xorg-server; i guess that's the command i did it with).

i was all happy - i could connect the second monitor.

BUT since then every fullscreen application change causes the backlight's turning off.

and since my hotkeys for changing brightness do not work, i consider this a big problem as i can launch no fullscreen applications (without risking serious damage to my eyes ;))

is there any chance of getting this bakc to work?

thank you in advance.

EDIT: i found out that the backlight turns off also when i turn on / off video playback. does that help at least a bit?

---

### Post by eidam655 on 2008-06-16
i have also found out that this issue cannot be observed under Windows XP.

i already tried another 'sudo dkpg-reconfigure xserver-xorg', but it didn't help.

at once i thought that the problem is solved by enabling CCSM. after the notebook restart, the backlight brightness was set at the same level as at the moment of turning off the laptop, but again when a fullscreen application or a video was launched it all went back to the darkness.

can anyone suggest any help? :(

thanks in advance

---

### Post by hotweiss on 2008-06-16
> **eidam655 said:**
> hello,

this weekend i could not connect my laptop to any external monitor/tv. so i tried and reconfigured the X server (with dkpg-reconfigure xorg-server; i guess that's the command i did it with).

i was all happy - i could connect the second monitor.

BUT since then every fullscreen application change causes the backlight's turning off.

and since my hotkeys for changing brightness do not work, i consider this a big problem as i can launch no fullscreen applications (without risking serious damage to my eyes ;))

is there any chance of getting this bakc to work?

thank you in advance.

EDIT: i found out that the backlight turns off also when i turn on / off video playback. does that help at least a bit?

See if this doesn't solve your brightness issue:


echo 0 > /sys/devices/platform/asus-laptop/ls_switch

If this solves your problem, use the following instructions to make this change automatic on boot:

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

---

### Post by eidam655 on 2008-06-16
no, it did not solve it...

it keeps saying 'Persmission denied' when trying to do the echo, the same with sudo echo, i cannot open the file with gedit nor with nano...

thank you for your answer though... are there any more ideas?

---

### Post by eidam655 on 2008-06-18
well, a progress has been made!

i looked into the logs and here's what i found:

> (II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a

this happens every time a video is launched.

i can post the whole Xorg.0.log if needed;

any help highly appreciated. thank you

---

### Post by eidam655 on 2008-06-22
whee!

all i had to do is to rewrite the config.

i loaded from liveCD, where everything worked and copied the config file and deleted all the lines that contained "vesa" in it and replaced all drivers with "i810"

viola! :)

if anyone  needed i can post the config file... but i think that this won't be necessary ;)

thx all for help

---

