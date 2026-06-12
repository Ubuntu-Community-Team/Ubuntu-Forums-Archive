---
title: "Lenovo Yoga 710 Ubuntu compatibility"
date: 2016-07-01
forum: Hardware
---

### Post by Geda on 2016-07-01
The yoga 710 14" is a new Lenovo model.. its like an upgrade to the yoga 700.
 is it compatible with ubuntu ? or is there any driver issues ?

---

### Post by epkphoto on 2016-07-03
See this discussion: [https://forums.lenovo.com/t5/Linux-Discussion/Yoga-710-How-to-install-Linux/td-p/3361544](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-710-How-to-install-Linux/td-p/3361544)

---

### Post by jusjusjus on 2016-07-12
I'm on Yoga **710-14ISK**, and got ubuntu 16.04 to run by [disabling acpi]("http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting").

---

### Post by dtom2 on 2016-09-15
Hi jusjusjus,

i am trying to sort it out also without success so far on my lenovo yoga 710 14isk. After installation did you face any other issues while having acpi disabled or everything worked ok? i read in another thread that someone faced isses with wifi and nic card.

thanks

---

### Post by izznogooood on 2017-02-06
[COLOR=#494949][FONT=&amp]I just bought this and had some issues, here's what i found.

Some might need a new BIOS, I used the normal one from late 2016:
[/FONT][/COLOR]https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Yoga-900-and-Ideapad-710S-Linux-Only-BIOS/ta-p/3466850[COLOR=#494949][FONT=&amp]

Update your BIOS (The fan appreciates it! trust me)[/FONT][/COLOR]
[COLOR=#494949][FONT=&amp]So, this has nothing to do with lenovo but with the linux kernel in general. [/FONT][/COLOR]

_***Dont disable ACPI***_
[COLOR=#494949][FONT=&amp]Linux will boot if you add the kernel parameter: [B][I]modprobe.blacklist=hid_sensor_hub
[/I][/B][/FONT][/COLOR]With stock 4.4 Kernel my i-7v7 boots in 3sec or less.
The battery with stock kernel is amazing, have not had kernel 4.10 more than a few days so have no idea about that yet.
If you are happy without the gyroscope just add this to your kernel parameteres in /etc/default/grub "***modprobe.blacklist=hid_sensor_hub quiet splash"***

[COLOR=#494949][FONT=&amp]If however you want the accelleromater to work you need to do some extra work. I am currently running Ubuntu 16.04 with this configuration (I imagine this would work independend on your distro with some minor mods to suit the distro):[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]You need to get a kernel newer than 4.10rc4 from the ubuntu mainline:[/FONT][/COLOR]
[COLOR=#494949][FONT=&amp][http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)[/FONT][/COLOR]
[COLOR=#494949][FONT=&amp]You no longer need to pass the kernel parameter. Adds a couple of seconds boot time but with flipp flopp screen who cares ;)[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]After you installed the kernel you need something that can monitor your sensor:[/FONT][/COLOR]
[COLOR=#494949][FONT=&amp][https://github.com/hadess/iio-sensor-proxy ]("https://github.com/hadess/iio-sensor-proxy")[/FONT][/COLOR]
[COLOR=#494949][FONT=&amp]This project is allready in the ubuntu repo's: [/FONT][/COLOR]
[COLOR=#494949][FONT=&amp]sudo apt install iio-sensor-proxy inotify-tools[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp][COLOR=#FF0000]_***NB:! You might have to put your computer to sleep and wake it up for the sensor to work. After that it keeps working.***_[/COLOR][/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]Then if you are running gnome 3.18 or newer you should be good to go. Gnome should detect your tilt and move accordingly.[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]If you are running unity you need to add a script. Follow the guide here with one exeption. Use my modified script as the original flips the screen wrong:[/FONT][/COLOR]
[COLOR=#494949][FONT=&amp][https://linuxappfinder.com/blog/auto_screen_rotation_in_ubuntu](https://linuxappfinder.com/blog/auto_screen_rotation_in_ubuntu)[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]Modified:[/FONT][/COLOR]

> #!/bin/sh
# Auto rotate screen based on device orientation

# Receives input from monitor-sensor (part of iio-sensor-proxy package)
# Screen orientation and launcher location is set based upon accelerometer position
# Launcher will be on the left in a landscape orientation and on the bottom in a portrait orientation
# This script should be added to startup applications for the user

# Clear sensor.log so it doesn't get too long over time
> sensor.log

# Launch monitor-sensor and store the output in a variable that can be parsed by the rest of the script
monitor-sensor >> sensor.log 2>&1 &

# Parse output or monitor sensor to get the new orientation whenever the log file is updated
# Possibles are: normal, bottom-up, right-up, left-up
# Light data will be ignored
while inotifywait -e modify sensor.log; do
# Read the last line that was added to the file and get the orientation
ORIENTATION=$(tail -n 1 sensor.log | grep 'orientation' | grep -oE '[^ ]+$')

# Set the actions to be taken for each possible orientation
case "$ORIENTATION" in
normal)
xrandr --output eDP1 --rotate right && gsettings set com.canonical.Unity.Launcher launcher-position Bottom ;;
bottom-up)
xrandr --output eDP1 --rotate left && gsettings set com.canonical.Unity.Launcher launcher-position Bottom ;;
right-up)
xrandr --output eDP1 --rotate normal && gsettings set com.canonical.Unity.Launcher launcher-position Left ;;
left-up)
xrandr --output eDP1 --rotate inverted && gsettings set com.canonical.Unity.Launcher launcher-position Left ;;
esac
done

---

### Post by MechEng70 on 2017-03-12
I have followed all the advice here and still can not get the touchscreen to work.  I can manually get the screen to rotate using the xrandr command (have to update the eDP1 to eDP-1).

1. updated BIOS firmware
2. running 4.10 kernel
3. using noirq and blacklisting the hid.
4. installed [COLOR=#494949]iio-sensor-proxy inotify-tools
[/COLOR]5. tried ubuntu-desktop and gnome desktops

any ideas on what to do next?  
 I would really like to get the touchscreen to work... :)
[COLOR=#494949]
[/COLOR]

---

