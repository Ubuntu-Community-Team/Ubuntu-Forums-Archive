---
title: "Have any software control monitor settings available in Ubuntu ?"
date: 2021-09-26
forum: Hardware
---

### Post by aug7744 on 2021-09-26
I had used the software below in another OS
[https://www.nirsoft.net/utils/control_my_monitor.html](https://www.nirsoft.net/utils/control_my_monitor.html)

Have any software that does the same feature in Ubuntu ?
The LCD monitor use VGA cable.

Thanks for reply.

---

### Post by Autodave on 2021-09-26
gddccontrol  might be what you are looking for.  I personally have never used it, so use at your own risk.  In fact, if you try it, please report back on how it works!

---

### Post by TheFu on 2021-09-26
If software doesn't exist, you can create multiple text config files (whichever are needed for the different settings), then swap those in using a script.  While I don't do it for video settings, I do for /etc/hosts contents.

I have 2 (or more) files that get copied into the main file when needed, then the subsystem that needs that config file gets restarted or sent a -HUP signal (that tells most daemon processes to re-read config files).

An overly simple script:

```
#!/bin/bash

FILE1="/etc/hosts.lan"
FILE2="/etc/hosts.travel"
TARGET="/etc/hosts"

#  The files are in /etc/, so normal userids cannot change/cp/mv/rm them
if [ $(id -u) -ne 0 ] ; then
    echo ERROR: Must run with sudo/root.
    exit 5
fi

# look for "lan" as the first parameter
if [ "$1" == "lan" ] ; then
 echo cp $FILE1 $TARGET
else  # anything except lan gets file2
 echo cp $FILE2 $TARGET
fi
```

To use it,
 
```
$ sudo  ~/bin/myscript lan
cp /etc/hosts.lan /etc/hosts

$ sudo  ~/bin/myscript w
cp /etc/hosts.travel /etc/hosts

```

You can get fancy and use getopts (built-in bash) and support lots of options just like all the other command-line tools.  You could have the script look at the current file, and toggle the other file without too much trouble. Just diff on one of them and if they match, it then copy the other file in.  If the test file didn't match, copy it into the main file location.  Then create a .desktop file and hook that into your menu.  Not hard at all, in under 512 bytes.  That's efficient compared to any fancy GUI tool.

Bash has a menu system built-in too, so if you don't want to force a command line option, but have a menu to choose options from, that's possible.  Look up the **select** built-in function.

So, if you connect different xorg files and xrandr commands, there is very little that cannot be accomplished.   Of course, this doesn't work for Wayland.  I haven't any clue about Wayland, except that it isn't X11 and doesn't use the normal X config files.

---

### Post by Holger_Gehrke on 2021-09-26
As somebody who uses ddccontrol to switch the input of my external monitor back and forth between my laptop and my Raspberry Pi and has played around with gddccontrol a bit I can tell you that it does the job. One thing you should know: since DDC and DDC/CI is (as far as the hardware implementation is concerned) an i2c bus you need to be able to read and write /dev/i2c-*. You must either run (g)ddccontrol with elevated privileges (sudo or pkexec) or add your account to the group 'i2c'.

Holger

---

