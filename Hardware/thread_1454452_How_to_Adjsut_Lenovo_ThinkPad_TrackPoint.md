---
title: "How to Adjsut Lenovo ThinkPad TrackPoint"
date: 2010-04-14
forum: Hardware
---

### Post by undoIT on 2010-04-14
I just got my new Lenovo ThinkPad T410s laptop. I loaded up Ubuntu 10.04 Lucid on it and most everything is working well. However, the TrackPoint (TrackStick) is slow and requires too much pressure to navigate. I found these instructions for adjusting speed and sensitivity:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed)

The instructions do not work. I tried echoing the commands and also adding the commands to rc.local. Is there another way to do this in Ubuntu Lucid?

---

### Post by undoIT on 2010-04-14
Okay. I found out that I had to drop into root before running the echo commands with this:

```
sudo su
```

Then I am able to make the adjustments but they only last for the session. It seems that rc.local is not working since the same commands have been added properly but do not take effect after reboot.

Any ideas?

---

### Post by undoIT on 2010-04-29
Okay, I created a script as described here:

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

Step 1 (create empty script):
```
kdesudo kate /etc/init.d/trackpoint
```

Step 2 (add to file and save):
```
#!/bin/sh
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
```

Step 3 (set permissions to execute for script):
```
sudo chmod +x /etc/init.d/trackpoint
```

Step 4 (set script to run):
```
sudo update-rc.d trackpoint defaults
```

The sensitivity and speed is still set to defaults when I reboot. Am I missing anything?

---

### Post by undoIT on 2010-05-08
Does anyone know a way to override this file with brute force so that it stops resetting every time the laptop is rebooted?

/sys/devices/platform/i8042/serio1/serio2/sensitivity

nothing seems to work.

---

### Post by willdeans on 2010-09-04
This is the script I use.  You may take some code from the script below and place it into your .bashrc if you are having problems with rc.local and you always open a shell straight away. 

#!/bin/bash

#
#    make the trackpoint faster
#

TRACKPOINT_DEVICE_DIR=/sys/devices/platform/i8042/serio1/serio2 

if test -e ${TRACKPOINT_DEVICE_DIR}
then
    if ! ensure_root
    then
        ssh root@localhost "$0"
        exit
    fi
    echo -n 250 > ${TRACKPOINT_DEVICE_DIR}/sensitivity
    echo -n 250 > ${TRACKPOINT_DEVICE_DIR}/rate
    echo -n 250 > ${TRACKPOINT_DEVICE_DIR}/speed
    echo -n 3 > ${TRACKPOINT_DEVICE_DIR}/inertia
else
    echo $0: cannot find trackpoint driver
fi

---

### Post by DesertF0x on 2010-10-06
Are you using Maverick? Is the Trackpoint configuration persistent after resume from standbye?

---

### Post by 4n1s on 2010-10-19
Hi,

the problem with suspend is that after each resume from stand-by, a new folder:
/sys/devices/platform/i8042/serio1/serioN+1

is created in place of (or in addition to) the original folder:
/sys/devices/platform/i8042/serio1/serioN

where N is initially is 2.


So I've created a brutal hack to make the settings recovered after resume:

1) create a file named trackpoint.sh in /usr/local/bin/
with the following code:
```

#!/bin/bash

#The new name for the trackpoint device will be stored in DIRNM
DIRNM=`ls -rt /sys/devices/platform/i8042/serio1/|grep serio|tail -n 1`

TPDIR=/sys/devices/platform/i8042/serio1/$DIRNM
echo $TPDIR
if [ -d "$TPDIR" ]; then
	echo -n 255 > $TPDIR/sensitivity
	echo -n 160 > $TPDIR/speed
	echo -n 1 > $TPDIR/press_to_select
else
	echo error $TMPDIR> /var/log/trackpoint_error
fi

```
this simply uses the newest name for the peripheral and updates its sensitivity, speed, etc.

2) create a file named: 10_trackpoint in /etc/pm/sleep.d/
and put this content inside of it:
```

#!/bin/bash
case "$1" in thaw|resume)
	sleep 10;
	/usr/local/bin/trackpoint.sh;
        ;;
    *)
        ;;
esac
exit $?

```
this runs the script /usr/local/bin/trackpoint.sh after each resume from suspend. Apparently the sleep is necessary to make it work, better ideas are of course welcome.


I've an even dirtier hack to recover also the middle-button scrolling functionality of trackpoint.

---

### Post by mathw on 2010-10-20
It makes a new device? I suppose that explains why my gpointing-device-settings shows me two trackpoints now. It doesn't explain why none of its settings persist over suspend though - including the disabling of the normal touchpad, which seems to turn off randomly during a session anyway.

Not best pleased with that, since it used to work just fine.

---

### Post by 4n1s on 2010-10-21
Well in my case it's creating a new device with the default settings, after each resume. So, after each resume it shifts back to the slow trackpoint default settings.

---

### Post by DesertF0x on 2010-10-24
There is a bugreport about this problem: [LINK]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/659712")

---

### Post by undoIT on 2010-10-24
The following worked for me:

```
gksudo gedit /etc/udev/rules.d/trackpoint.rules
```

add the following and save:

```
SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity", ATTR{sensitivity}="250", ATTR{speed}="140"
```

works after suspend. the only side-effect is that there is a pause at the login window (i have an SSD drive so the boot is very fast). the cursor blinks maybe 8 or 9 times before i can type in my password.

btw, i tried out Fedora 14 beta and multi-gesture (two-finger scroll / two-finger right click) is functioning properly on my thinkpad t410s. it's too bad that *buntu maverick doesn't support this yet.

---

### Post by map84 on 2010-11-11
I'm using Maverick and trying to adjust my trackpoint as well (Lenovo X100e).

my /etc/rc.local:
```
sudo echo -n 200 > /sys/devices/platform/i8042/serio4/serio5/speed
sudo echo -n 200 > /sys/devices/platform/i8042/serio4/serio5/sensitivity
sudo echo -n 200 > /sys/devices/platform/i8042/serio4/serio5/rate
sudo echo -n 3 > /sys/devices/platform/i8042/serio4/serio5/inertia

```

using this commands sometimes work, but every third reboot I have to adjust the trackpoint manually, because the system pretending that the directory

```
/sys/devices/platform/i8042/serio4/serio5/speed
``` is **nonexistent**

Does anybody know what I should do?

---

### Post by dm187 on 2010-12-17
I have been going crazy for a little while with my Thinkpad X200 running Ubuntu 10.10, it turns out I just did not play around enough with the sliders in the System -> Preferences -> Mouse menu check out the picture, note the sensitivity and acceleration settings. This is ubuntu guys, remember that, no need to type in commands or edit text files!!!

---

### Post by Closrapexa on 2011-10-30
This may be an old thread, but I have a related question. When setting 

```
echo -n 255 > /sys/devices/platform/i8042/serio1/speed
echo -n 255 > /sys/devices/platform/i8042/serio1/sensitivity
```

in the rc.local fileit works just fine, but my problem is with the wheel emulation on the middle button of the trackpoint, especially in firefox. In order to disable this, I have to open gpointing-devices, select and then de-select wheel emulation, and then the scrolling is smooth. This resets on reboot. Is there any way to add another line in the rc.local file, or somewhere else so that this will not be reset on reboot?

---

### Post by NaOH on 2012-01-10
Thank you!  This was driving me nuts.  This approach works perfectly on 11.10 on a ThinkPad T410.  So far this has stuck after several reboots and a numerous suspend/awakenings.


> **undoIT said:**
> The following worked for me:

```
gksudo gedit /etc/udev/rules.d/trackpoint.rules
```

add the following and save:

```
SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity", ATTR{sensitivity}="250", ATTR{speed}="140"
```

works after suspend. the only side-effect is that there is a pause at the login window (i have an SSD drive so the boot is very fast). the cursor blinks maybe 8 or 9 times before i can type in my password.

btw, i tried out Fedora 14 beta and multi-gesture (two-finger scroll / two-finger right click) is functioning properly on my thinkpad t410s. it's too bad that *buntu maverick doesn't support this yet.

---

