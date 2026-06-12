---
title: "Need to control nVidia GPU Fanspeed"
date: 2013-02-10
forum: Hardware
---

### Post by ooleyguy on 2013-02-10
I have an EVGA nVidia 550 GT Ti video card and am running Ubuntu 12.04.1 with the 304.64 nVidia drivers installed. By default, the fan runs at about 20% speed. There is no place in nvidia-settings to change fan speed. In Windows, I used a program by EVGA called Precision X to control the speed.

I tried to use an xorg.conf file to add "coolbits"    "4" to enable some supposed hidden settings in nvidia-settings, but it just made my system unusable and I had to boot in recover mode to delete the file I created. I tried the file in home/[USER], etc/X11, and usr/share/X11/xorg.conf.d and the same thing happened or nothing at all changed.

Is there a GUI program that will let me change this setting or can someone give me some help with a way to make an xorg.conf file that doesn't crash the system.

---

### Post by Yellow Pasque on 2013-02-11
> **ooleyguy said:**
> By default, the fan runs at about 20% speed.

Does it always stay at that speed, even when you're running something graphically intensive and the GPU gets warm?

---

### Post by Yellow Pasque on 2013-02-11
[http://en.gentoo-wiki.com/wiki/Nvidia#Manual_Fan_Control_for_nVIDIA_Settings](http://en.gentoo-wiki.com/wiki/Nvidia#Manual_Fan_Control_for_nVIDIA_Settings)

FWIW, I don't think Coolbits works on GTX 500/600 cards on Linux: [http://www.phoronix.com/scan.php?page=news_item&px=MTE2MTU](http://www.phoronix.com/scan.php?page=news_item&px=MTE2MTU)

---

### Post by ooleyguy on 2013-02-11
The speed never changes. It never changed in Windows 7 either unless I used EVGA's app. I might try it in WINE, but I doubt it will do anything. I had to have it running as a background app in Windows for the fans speed to change.

---

### Post by ooleyguy on 2013-02-11
Ok, I am almost there.

Thank you, Temüjin! That website didn't exactly show me the way, but it did get me searching in the right place. Here's the steps I took to enable fan control in the nvidia-settings.


[LIST=1]
[*]Type gksu nautilus in Terminal and allow your group read/write access to /etc/X11 (or use the chmod commands if you prefer the terminal.
[*]Type nvidia-settings into the terminal and in the NVIDIA X Server Settings window that pops up, click on nvidia-settings Configuration and then click "Save Current Configuration" and then exit the applicationThis will create ~/.nvidia-settings-rc for you. (not 100% sure this is needed)
[*]Type nvidia-xconfig into the terminal. This will create an /etc/X11/xorg.conf file that does not, by default, get created in 12.04 Precise.
[*]Type nvidia-xconfig -- cool-bits=4 into the terminal and this will add the proper settings in your /etc/X11/xorg.conf file and back the previously created one up.
[*]Reboot your machine and open nvidia-settings up with the Terminal or your dash and under your GPU heading/Thermal Settings list, you can now change fan speed.
[*]I yanked mine up to 100% from 20% and my temperatures went from 47C to 35C.
[/LIST]
Remember to change the permissions on the /etc/X11 directory back so accidents don't happen.

My only problem now is how to set the fan to 100% at startup. I currently have to manually enter the settings and change them or do it in the terminal. I know you can use some sort of scripting, BASH, I think to do things. Can one of those scripts be used to automatically run 

nvidia-settings    -a "[gpu:0]/GPUFanControlState=1"

and

nvidia-settings    -a "[fan:0]/GPUCurrentFanSpeed=100"

I'm still new to linux in general, but I made tons of .bat scripts back in my old DOS days.

BTW, putting those commands into a new ~/.xsession and .xinitrc did not work. I had to create them from scratch as 12.04 did not create them for me.

---

### Post by ooleyguy on 2013-02-11
Ok, completely solved. It may not be the most elegant way to do it but... Made a BASH script named FanController.sh with:

```
#!/bin/bash
nvidia-settings -a [gpu:0]/GPUFanControlState=1
nvidia-settings -a [fan:0]/GPUCurrentFanSpeed=100
```and added it to Startup Applications

---

