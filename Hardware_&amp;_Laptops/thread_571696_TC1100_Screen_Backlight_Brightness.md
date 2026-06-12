---
title: "TC1100 Screen Backlight Brightness"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by nickwu2000 on 2007-10-09
I have an HP TC1100, and for years it's been impossible to change the backlight settings in linux - changing the gamma doesn't actually help in terms of battery life, and so the usual advice was usually of little use.

However I recently discovered that the backlight can be changed, though I really don't understand why. I thought I'd post what I did here to help whoever else might be in the same situation, and maybe someone that knows a lot more about all of these could 'enlighten' us all about why this works!

Open up a console and type:

```
echo 0 > /proc/acpi/wmi/WMID/bluetooth
```

Then play with the toggle at the top (which is usually the scroll up/scroll down, xev doesn't report any events for me to tell you what is happening).

I'm so glad my battery life is now extended, and my eyes are straining.

Nick

---

### Post by robnz on 2007-10-10
Your suggestion doesn't wok for me. Not that I expected it to - very strange indeed. If you've installed the nvidia restricted drivers then simply type
```
$ nvidia-settings
```
Then under xserver-color-correction you can adjust the brightness.

---

### Post by robnz on 2007-10-10
You can set the brightness from the command line using the commands
```
$ nvidia --assign RedBrightness=XX
$ nvidia --assign GreenBrightness=XX
$ nvidia --assign BlueBrightness=XX
```
where XX is the brightness level from -1 to +1. Zero is the driver default. Positive numbers are brighter. Negative is dimmer. If anyone can figure out how to query the current setting I'd produce a script to dim/brighten a little at a time.

---

### Post by robnz on 2007-10-10
For the benefit of myself and other TC1100 users I've written a script to change the LCD brightness using the nvidia restricted driver in xorg.

Before running the dimmer script you must first run the nvidia-settings GUI and quit. This saves a copy of the current driver settings to ~/.nvidia-settings-rc. This was the only way I could find to keep track of the current brightness as it doesn't seem to appear anywhere in /proc.

Save the script below in your path and make it executable with chmod +x. Then map it to a key sequence of you choice. I use Windows+'-' for dimmer and Windows+'=' for brighter.

I threw this together last night and tidied it up today during lunch. While it works for me it has not been widely tested and your experience might be different to mine. Fixes/suggestions are welcomed.
```
#!/bin/sh
# dimmer.sh
# written by Rob Stockley (rob dash stockley at mowgli dot net dot nz) 
# to incrementally change the LCD brightness on a Compaq TC1100 tablet.
# Tested only with Kubuntu 7.04. All comments and suggestions welcome.

# first need to establish whether config file exists and we can write to it
NV_CONFIG="$HOME/.nvidia-settings-rc"
if ! [ -w $NV_CONFIG ]; then
    echo "$NV_CONFIG is either missing or not writable. Before you run this script you need to run the nvidia-settings GUI application. When you quit the GUI the current driver settings should be written to $NV_CONFIG."
    exit 0
fi

# now need to read current brightness values
CUR_R=`grep RedBrightness $NV_CONFIG | awk 'BEGIN { FS = "=" } ; { print $2 }'`
CUR_G=`grep GreenBrightness $NV_CONFIG | awk 'BEGIN { FS = "=" } ; { print $2 }'`
CUR_B=`grep BlueBrightness $NV_CONFIG | awk 'BEGIN { FS = "=" } ; { print $2 }'`

# stepping 0.2 gives me five dim and five bright settings
STEP="0.2"
case $1 in
    --reset)
        # reset to driver defaults
        NEW_R='0.0000'
        NEW_G='0.0000'
        NEW_B='0.0000'
        ;;
    --dec)
        # decrease brightness and check limits
        NEW_R=`echo "scale=4; $CUR_R - $STEP" | bc`
        if [ `echo "scale=4; $NEW_R < -1.0" | bc` -eq 1 ]; then
            NEW_R=-1.0
        fi
        NEW_G=`echo "scale=4; $CUR_G - $STEP" | bc`
        if [ `echo "scale=4; $NEW_G < -1.0" | bc` -eq 1 ]; then
            NEW_G=-1.0
        fi
        NEW_B=`echo "scale=4; $CUR_B - $STEP" | bc`
        if [ `echo "scale=4; $NEW_B < -1.0" | bc` -eq 1 ]; then
            NEW_B=-1.0
        fi
        ;;
    --inc)
        # increase brightness and check limits
        NEW_R=`echo "scale=4; $CUR_R + $STEP" | bc`
        if [ `echo "scale=4; $NEW_R > 1.0" | bc` -eq 1 ]; then
            NEW_R=1.0
        fi
        NEW_G=`echo "scale=4; $CUR_G + $STEP" | bc`
        if [ `echo "scale=4; $NEW_G > 1.0" | bc` -eq 1 ]; then
            NEW_G=1.0
        fi
        NEW_B=`echo "scale=4; $CUR_B + $STEP" | bc`
        if [ `echo "scale=4; $NEW_B > 1.0" | bc` -eq 1 ]; then
            NEW_B=1.0
        fi
        ;;
    --help)
        echo "Script: $0"
        echo "Purpose: Change the LCD brightness on a"
        echo "Compaq TC1100 using Nvidia restricted driver. "
        echo "Written by Rob Stockley, October 2007"
        echo
        echo "Usage: $0 [ --reset | --dim | --inc | --help ]"
        echo "Options:"
        echo "  --dec     decrease the brightness a little"
        echo "  --inc     increace the brightness a little"
        echo "  --reset   reset to standard brightness" 
        echo "  --help    print this message"
        exit 0
        ;;
    *)
        echo "Usage: $0 [ --reset | --dim | --inc | --help ]"
        exit 0
        ;;
esac

# fix cases where bc leaves us with leading -.
NEW_R=`echo $NEW_R | sed 's/-\./-0\./'`
NEW_G=`echo $NEW_G | sed 's/-\./-0\./'`
NEW_B=`echo $NEW_B | sed 's/-\./-0\./'`

# if we get to here then patch the .nvidia-settings-rc
patch -s $NV_CONFIG << EOF
--- .nvidia-settings-rc	2007-10-10 21:45:26.000000000 +1300
+++ .nvidia-settings-rc.new	2007-10-11 10:00:52.000000000 +1300
@@ -33,9 +33,9 @@
 0/FSAAAppControlled=1
 0/LogAnisoAppControlled=1
 0/GPUScaling[DFP-0]=131073
-0/RedBrightness=$CUR_R
-0/GreenBrightness=$CUR_G
-0/BlueBrightness=$CUR_B
+0/RedBrightness=$NEW_R
+0/GreenBrightness=$NEW_G
+0/BlueBrightness=$NEW_B
 0/RedContrast=0.000000
 0/GreenContrast=0.000000
 0/BlueContrast=0.000000
EOF

# finally the nvidia driver needs to load the new configuration
nvidia-settings -l

```

---

### Post by nickwu2000 on 2007-10-14
> **robnz said:**
> Your suggestion doesn't wok for me. Not that I expected it to - very strange indeed. If you've installed the nvidia restricted drivers then simply type
```
$ nvidia-settings
```
Then under xserver-color-correction you can adjust the brightness.

Thanks robnz; I forgot to mention that the echo needs to be committed as root, since you need to be able to access /proc/acpi/wmi/WMID/bluetooth

Your suggestion changes the screen pixel brightness, which isn't quite the same as what happens when I play with my toggle - for me, it's the **backlight** that changes brightness, not just the pixels on the screen. I'm still confused as to why this is working!

---

### Post by robnz on 2007-10-15
My HP/Compaq TC1100 is running Kubuntu 7.04 pretty much out of the box apart from a few customisations around the wacom tablet driver. Your fix doesn't work for me.
```
rob@rob-laptop:~$ ls -l /proc/acpi/wmi/WMID/bluetooth
-rw-r--r-- 1 root root 0 2007-10-15 19:50 /proc/acpi/wmi/WMID/bluetooth
rob@rob-laptop:~$ sudo echo 0 > /proc/acpi/wmi/WMID/bluetooth
bash: /proc/acpi/wmi/WMID/bluetooth: Permission denied
```

Also xev reports the jog shuttle button as next/prior on my tablet. I'm curious as to why our tablets are behaving so different. Please confirm your tablet is an HP/Compaq TC1100 and please also confirm which version of ubuntu you are running and how you installed it (fresh install or dist upgrade).

---

### Post by nickwu2000 on 2007-10-15
> **robnz said:**
> My HP/Compaq TC1100 is running Kubuntu 7.04 pretty much out of the box apart from a few customisations around the wacom tablet driver. Your fix doesn't work for me.
```
rob@rob-laptop:~$ ls -l /proc/acpi/wmi/WMID/bluetooth
-rw-r--r-- 1 root root 0 2007-10-15 19:50 /proc/acpi/wmi/WMID/bluetooth
rob@rob-laptop:~$ sudo echo 0 > /proc/acpi/wmi/WMID/bluetooth
bash: /proc/acpi/wmi/WMID/bluetooth: Permission denied
```


I also get this (I have the feeling it's because sudo isn't realising that we want to access /proc as root), so I have to do

```

sudo su - 

```

first, to get into root mode, and then from there I'm able to type in
```

echo 0 > /proc/acpi/wmi/WMID/bluetooth

```



> 
Also xev reports the jog shuttle button as next/prior on my tablet.


Oddly, xev reports the jog button for me too prior to the echo command - after that, it doesn't register in xev at all.


> 
 I'm curious as to why our tablets are behaving so different. Please confirm your tablet is an HP/Compaq TC1100 and please also confirm which version of ubuntu you are running and how you installed it (fresh install or dist upgrade).

My tablet is the HP TC1100, using 7.04, fresh install as well.

---

### Post by robnz on 2007-10-15
Okay, I can now confirm that our tablets are behaving the same. Switching to root (as opposed to using sudo) made the difference. It appears that the TC1100 may require some customisation of the acpi driver.

UPDATE: A quick google tuns out that the HP/Compaq acpi implementation is not compliant with the open acpi standard. I guess our mileage will vary.

---

### Post by nickwu2000 on 2007-10-20
Sadly this "feature" has died a death with the new Ubuntu 7.10. If anybody finds a way of getting it back, I'd love to hear about it.

---

### Post by DanRenfro on 2007-10-28
I was able to get the TC1100 backlight to adjust (brighter and dimmer) with the rocker in Ubuntu 7.10. As root:
modprobe tc1100-wmi
echo 0 > /proc/acpi/wmi/WMID/bluetooth

>>toggle the rockerswitch up and down to adjust the brightness

echo 1 > /proc/acpi/wmi/WMID/bluetooth

>>rockerswitch now functions normally again (keycodes are emitted)

This is with the proprietary nvidia drivers... i haven't tested it otherwise, but this is one of the main features I've wanted back since I switched my tablet to linux.  Until now, none of the different methods I've found (and other people have found to work) worked on -my- tablet. 

This kinda make my day!

---

### Post by nickwu2000 on 2007-10-28
Hurrah! 

This works for me too. I'm glad the brightness controls are back :) Thanks DanRenfro

---

### Post by phenest on 2007-11-07
Again, does anyone know why this works? The module (judging by its name) appears to be specifically for this make and model of computer, therefor it must be possible to implement brightness control properly (and all the other stuff this module provides).

I added tc1100-wmi to /etc/modules and then:
```
echo 0 > /proc/acpi/wmi/WMID/bluetooth
```
to see if it would survive a reboot. Guess what? It does! That makes the toggle switch much more useful.

I think this module was written by some guys at HP and Intel for Linux, so someone must have the source code for it and implement it better. I'm a programmer, so if I had the code, I'd have a go myself.

---

### Post by popch on 2007-11-10
Sending bytes to this address turns a switch in the hardware cirquitry on and off, causing the rocker switch to perform different actions.

I wonder if there are other useful values besides 0 and 1, but I am too chicken to try it.

---

### Post by pablojavier on 2007-11-12
Hi!

Just to make a little summary from the great discoveries done here. To enable bightness adjustment on TC1100 you should:

[LIST=1]
[*]Open a terminal and execute ```
gedit /etc/modules
```
Add the following line to the end of that file:
[INDENT]tc1100-wmi[/INDENT]
[*]Open a terminal and execute ```
gedit /usr/bin/adjust_screen.sh
```
Paste the following into that file:
```
#!/bin/sh
if [ -n "$(cat /proc/acpi/wmi/WMID/bluetooth | grep off)" ]; then
        echo 0 > /proc/acpi/wmi/WMID/bluetooth
else
        echo 1 > /proc/acpi/wmi/WMID/bluetooth
fi

```
[*]Restart Ubuntu (or execute *modprobe tc1100-wmi*)
[*]From now on, executing *adjust_screen.sh* will toggle the rocker switch between the normal function (page up-down) and brightness adjustment.

[/LIST]

Next step: making a Q-menu like that includes all the scripts available till date (Screen rotation, brightness adjustment, etc). Who will pick that glove up? :)

Cheers,
Pablo

---

### Post by phenest on 2007-11-13
> **pablojavier said:**
> From now on, executing *adjust_screen.sh* will toggle the rocker switch between the normal function (page up-down) and brightness adjustment.

But this still needs to be executed from root:
```
sudo sh adjust_screen.sh
```
I don't want to keep entering my password just to adjust the screen brightness.

---

### Post by phenest on 2007-11-14
I don't want to post off topic, so I'm going to post about the 'Q' menu on my TC1100 tutorial. Just follow the link in my signature.

---

### Post by Aearenda on 2008-05-27
Just in case anybody is trying this in Hardy, it won't work. It seems the tc1100-wmi module is missing. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212513](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212513).

EDIT: See [http://wiki.linuxquestions.org/wiki/Tc1100#Kernels_2.6.23_and_2.6.24_.28Ubuntu_8.04_Hardy_LTS.29](http://wiki.linuxquestions.org/wiki/Tc1100#Kernels_2.6.23_and_2.6.24_.28Ubuntu_8.04_Hardy_LTS.29) for how to compile a new kernel to make it work again. Don't forget to compile the corresponding nvidia module too.

---

### Post by Tweenk on 2008-05-28
You can also install the Intrepid version of the kernel as detailed in the bug report, I added some info about this to the linked LQWiki page.

Additionally, there were some wrong responses in this thread, so I'll correct them:
1. Using the brightness control built into the nvidia driver will not reduce ower consumption. It just changes the colors displayed on the screen, but doesn't affect the amount of power supplied to the backlight.
2. Using things like:
```
sudo echo 0 > /proc/acpi/wmi/WMID/bluetooth
```
won't work, because this is what really happens:
i. The shell executes the command: "sudo echo 0",
ii. Then, the output is written to the file /proc/acpi/wmi/WMID/bluetooth
**The second operation is executed by the shell, not by sudo.** Since the shell runs as an unprivileged user (you), the second operation will fail. If you want to do shell redirections with sudo, the correct way to do this is:
```
sudo sh -c 'echo 0 > /proc/acpi/wmi/WMID/bluetooth'
```
This way, the steps are:
i. The command sh (shell) is started as root.
ii. The shell executes the command: "echo 0".
iii. Then, the sudoed shell writes the output to /proc/acpi/wmi/WMID/bluetooth
In this case, the shell is running as root when it tries to write to the file, so the operation succeeds.
Note, however, that the new WMI driver creates the files /sys/devices/platform/tc1100-wmi/wireless and /sys/devices/platform/tc1100-wmi/jogdial as writable for everyone, so you don't need to do any of this magic.

---

