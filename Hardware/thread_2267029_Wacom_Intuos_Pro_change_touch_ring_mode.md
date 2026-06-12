---
title: "Wacom Intuos Pro change touch ring mode?"
date: 2015-02-26
forum: Hardware
---

### Post by CyberAngel on 2015-02-26
I am on Kubuntu 14.04 and I just bought a Wacom Intuos Pro Medium.
The tablet is recognized by the system, but initially I could not configure the different keys and profiles in KDE settings.
This is fixed by following the procedure described here: [https://answers.launchpad.net/ubuntu/+source/wacomtablet/+question/229153](https://answers.launchpad.net/ubuntu/+source/wacomtablet/+question/229153)

So now the tablet works very nicely, but I have one question.

The tablet has 4 different modes for the touch ring and 4 different leds around the touch ring indicating which mode is active as one can see in the manual.
I attach the corresponding page:
[ATTACH=CONFIG]260299[/ATTACH]

Currently, I can only configure one action for the touch ring (Ring Up/Ring Down) in my KDE settings, and I cannot find any option to change modes.
Also, the upper left led is always on and the other three leds are off, since that's the default mode and I cannot change it.

Does anyone know if it is possible to configure different touch ring modes and actions on each mode on Linux, and change between the modes while having the active mode reflected by the different leds?

---

### Post by CyberAngel on 2015-02-26
hmmmmm

It looks like I am facing this bug: [http://sourceforge.net/p/linuxwacom/bugs/275/?limit=25](http://sourceforge.net/p/linuxwacom/bugs/275/?limit=25)

If I connect a USB cable, there is a folder "/sys/bus/usb/devices/*/wacom_led/".

There is a file that if I change its contents (0, 1, 2, 3), different leds are turning on.

However, if I use the wireless connection, there is no such directory!

I guess I will have to compile the latest drivers from source and see what's happening.

Then, there is a script here: [http://registry.gimp.org/node/28096](http://registry.gimp.org/node/28096) that looks like it is doing what I am asking for.

Also it looks like KDE Graphic Tablet settings do not support the configuration of different modes, so I might have to do it from the console.

I will test tomorrow and report back on my findings.

---

### Post by CyberAngel on 2015-03-03
Here is my solution:

1. Installed the latest input-wacom drivers. Now the status_led0_select file appears for both USB and Wireless connection :)
2. Blacklisted the original modules so that my modules are loaded.
3. Added a udev rules file to give read/write permissions to simple users to modify the **/sys/bus/usb/devices/*/wacom_led/status_led*_select** file.
4. Created a Generic python script based on the GIMP Wacom script, that the user can add different modes for different profiles. The profile names in the python script should match the created profiles in kcm_wacomtablet. **qdbus org.kde.Wacom /Tablet org.kde.Wacom.getProfile** is used to read the current profile used by the kcm_wacomtablet, and the corresponding modes are activated when the script is executed.
5. The python script supports up to 4 modes per profile (since my Wacom Intuos Pro Medium has 4 LEDs to indicate different Touch-ring modes). Each time the script is called, it will toggle through the available modes (one at a time). How many modes are supported can easily be changed by changing a variable in the script (if your tablet has more mode indication LEDs)
6. Assign a global KDE shortcut to execute the script as shown in the following 3 screenshots:
[ATTACH=CONFIG]260427[/ATTACH]

[ATTACH=CONFIG]260426[/ATTACH]

[ATTACH=CONFIG]260425[/ATTACH]
7. Assign Button 1 in kcm_wacomtable (or any other button that you want) of your Wacom tablet to the global shortcut that executes the script.
8. Enjoy :)

You can get one script to easily install/uninstall the latest wacom drivers with DKMS support (so each time a new kernel is installed, the drivers are recompiled for the new kernel automatically) and the python script to toggle through different Touch-ring modes at: [https://github.com/cyberang3l/input-wacom-dkms](https://github.com/cyberang3l/input-wacom-dkms)

Both of the scripts contain comments, so make sure to read them if you are interested to use them.

---

