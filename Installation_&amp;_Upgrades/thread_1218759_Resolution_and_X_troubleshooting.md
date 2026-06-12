---
title: "Resolution and X troubleshooting"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by xphill64x on 2009-07-21
Hi, I seem to have a resolution problem, I'm stuck in 1024*768, and can't get X to read the other modes. This happened after upgrading from 8.04LTS to 9.04 the other day. I had a similar problem around Christmas - but I can't really remember how I resolved that aside from very dumb luck.


I have a GeForce 4 MX video card and a 22.1' widescreen Westeringhouse LCD monitor. Currently set to 1400x900 via Nvidia X Server Settings (which don't stick). System information for monitor says that it's at 1440x900@60Hz.

Windows uses a 1600x900 resolution.

When I try saving the Nvidia X Server settings xorg.conf - it crashes X usually, saying no screens are found.

Here's a copy of the xorg.conf that Nvidia set up.
[http://pastebin.com/m1b8559fc](http://pastebin.com/m1b8559fc)

It also seems that my WM isn't acting right - going within a few inches of the bottom of screen - opening up menu's makes them "launch up" like they hit a border. Here's a screenshot of that.

[http://yfrog.com/b2screenshotsamp](http://yfrog.com/b2screenshotsamp)

I'm going to reset X and give ya'll a log file of X11 crashing with the Screens found, none have a usable configuration error. I had to monkey around to get X to start so I could write this. I think I ran the sudo dpkg-reconfigure xserver-xorg command to get it to start the GDM - but again, the resolution wasn't set up properly.

If you don't know how to solve it, but do know how to probe for correct VREFRESH and HSYNC settings - that would be great, I have a feeling that's my problem. (I have googled to no avail)

I've also tried looking up the native resolution online to no avail, WestingHouse Digital sucks at keeping information online for their monitors. And I can't find the box - though I can check the garage sometime tomorrow (Though I doubt I'll find it)

==Note:==
This is about problems encountered after upgrading to 9.04 - if it would be better placed somewhere else - perhaps in Gnome or some other sub-forum, please move it there, or tell me and I'll eventually repost it. (Don't delete, I really, really, don't want to type this all up again)

---

### Post by xphill64x on 2009-07-21
This is the xorg.0.log that was produced when I first turned on the system a few moments ago.

[http://pastebin.com/f50f2be3a](http://pastebin.com/f50f2be3a)

It's like it's not reading my modepath and just figuring it out what it wants through something else.

---

### Post by xphill64x on 2009-07-21
Tracking similar bugs on launchpad have told me to include the following:

Output from lspci -vn
[http://pastebin.com/fa4c2d2c](http://pastebin.com/fa4c2d2c)

Output from sudo xresprobe nvidia:
```
id: L2220HW
res: 1920x1080 1680x1680 1600x1200 1440x1440 1280x1024 1024x768 800x600 720x400 640x480
freq: 31-82 56-76
disptype:
``` 

Output from sudo vbetool vbefp panelsize:
```
Panel id read failed

```

Output from sudo ddcprobe:
[http://pastebin.com/f4e84fa84](http://pastebin.com/f4e84fa84)

And, output from cat /var/lib/acpi-support/*-*:
TCB418G
System Manufacturer
Product Name
SYS-xxxxxx

---

### Post by xphill64x on 2009-07-22
Ops, seems like this is a won't fix:

Thanks to anyone who took the time to read this, I'll just have to screw around with the nv drivers or something. Or just turn this into a really big router with Vyatta.

[http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

If anyone wishes to close this, that's cool, I have a few old tricks I can still use probably to get it to work later.

---

### Post by starcannon on 2009-07-22
**READ ENTIRELY BEFORE BEGINNING**

First I would try the hardware driver utility drivers, and give configurating them once more another try:

[LIST=1]
[*]Purge all previously installed drivers.
[*]Menu: System>Administration>Hardware Drivers
[*]Enable your drivers
[*]Reboot when requested
[*]Menu: System>Preferences>Screen Resolution
[*]Select desired resolution from drop down list and apply changes.
[*]If desired resolution is not present continue on with this bulleted list of instruction.
[*]CTRL-ALT-F1
[*]login
[*]sudo /etc/init.d/gdm stop
[*]sudo nvidia-xconfig
[*]reboot
[*]Is screen resolution correct? If yes stop here, if no continue on.
[*]Menu: Applications>Accessories>Terminal
[*]sudo apt-get install nvidia-settings
[*]Alt+F2
[*]gksu nvidia-settings
[*]Click on "X Server Display Configuration" in the left menu.
[*]Choose your resolution, apply and save changes.
[*]Possible log out/log in or reboot required for changes to take effect.
[/LIST]

If that doesn't work, I would try purging the synaptic nvidia drivers and then installing the latest driver from the nvidia website for that card; nvidia claims the latest driver has fixes for the newer kernels, its probably where I would start, but it requires more maintanence on your part any time there is a kernel update you have to reinstall the driver when doing it this way.
[http://www.nvidia.com/object/linux_display_ia32_96.43.13.html](http://www.nvidia.com/object/linux_display_ia32_96.43.13.html)


[LIST=1]
[*]Print these instructions.
[*]CTRL-ALT-F1
[*]login
[*]sudo /etc/init.d/gdm stop
[*]cp /etc/X11/xorg.conf ~/xorg.conf.bak
[*]sudo rm /etc/X11/xorg.conf
[*]cd /path/to/nvidia/driver.bin
[*]chmod a+x ./driver_name.bin
[*]sudo apt-get install build-essential
[*]sudo ./driver_name.bin
[*]Answer to the affirmative for all questions, ignore errors unless it terminates the install process.
[*]reboot
[/LIST]
I think that is a legacy card, I'm not certain though; nvidia-settings may or may not be available to your driver set, if it is, its a great tool.
Here is another Driver install guide for the newer cards; but, may be worth looking at to see if anyone has had your same issue. [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

Good Luck

---

### Post by xphill64x on 2009-07-22
Believe it or not, I'm pretty sure I did all that; though, I'm not sure if I "purged" the previous before doing it. I'll give it a shot later though. Thanks for the help!

>I did the Restricted Install/Uninstall

>Tried nvidia-settings

>Installed from online, did the kernel thing.

Know where I can get 8.04LTS again?

---

### Post by starcannon on 2009-07-22
You can get 8.04LTS here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

And personally I think that is the best option, particularly when running legacy hardware. I had some 9.04 issues myself, and some 8.10 issues too. I only use the tweenleases when it fixes something on a more modern piece of hardware; currently laptops i use 8.10, and netbooks i use 9.04. Desktops and Legacy I stick with 8.04 /shrug, thats the system that keeps me working/playing/wasting time on the interwebs, instead of installing, configuring, etc...

GLaHF

---

### Post by xphill64x on 2009-07-22
Good deal, thanks.

---

