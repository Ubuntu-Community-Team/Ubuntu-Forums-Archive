---
title: "Joystick calibration problems."
date: 2011-04-08
forum: Hardware
---

### Post by vedovatti on 2011-04-08
Hi,

I need help because there is not a lot of information about the joystick on the new ubuntu releases. So my problem are various. I have a HP tm2 that has an accelerometer that is detected as joystick. And I want to calibrate another joystick I have.

I am a user of your program Jstest on Ubuntu 10.10, I just wanted to ask you about chosing device. Unfortunately I have  tried to install a Joystick using Jstest-gtk and I found out that on  the /dev/input/js0 was detected ST LIS3LV02DL Accelometer. And my  joystick was on js1 This is a feature, not a bug. The idea is to let people play pinball with their laptops. 

Anyway the problem is that jstest doesn't list more than one joystick. On the feature of your program says that it supposed to but I cannot calibrate my joystick because it just shows the js0 that is occupied by the accelometer. Could please tell me how to change to the other device or if its a bug from the program that doesnt show more than one joystick?

I tried do on the terminal: ```
jstest-gtk /dev/input/js1. 
```

I get from the system: 
> terminate called after throwing an instance of 'Glib::FileError'
Aborted
Warning: unknown joystick, not displaying graphical representation.

No luck on that. I tried the same command with js0 and got the same answer (even though is plugged). On the other hand the program supposed to show all the joystick connected as you say but the window doesn't appear. Maybe it is just affecting Ubuntu 10.10 or my PC. I check with about the permissions I tried the commands as superuser I got the same as above. And the /dev/inpus/js0 and js1 have just root permissions. 
[B]
First problem: the jstest-gtk doesn't show the window where you can select the device.[/B]

As a work around. I plugged the my joystick before the computer starts and it gets on the js0 and the accelerometert gets the js1. In this case I could calibrate it. When I unplug the joystick(when is js0) and restart the program the accelormeter is detected as js1. So it basically could be a bug from the window that choose the devices js. I would like to know if affects the ubuntu distribution or is just my pc.

After this workaround comes my second problem. I was able to calibrate both of the joystick (the real one and the accelerometer) but everytime I boot the system it just forget the parameter.

**Second problem: Save the calibration settings for the joysticks.**

Anyway I would really appreciate help for this thanks.

---

