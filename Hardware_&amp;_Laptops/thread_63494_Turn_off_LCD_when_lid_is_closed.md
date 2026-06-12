---
title: "Turn off LCD when lid is closed"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by xx404 on 2005-09-08
I'm trying to get my LCD panel to trun off when I close the lid on my notebook. I've written the appropriate APCI scripts and they are being run when the lid is opened and closed but I'm having trouble with permissions and the xset command.

The script that is being run is in /etc/acpi/local and is owned by root and is executable. The command I am using to turn off the LCD is

/usr/X11R6/bin/xset dpms force off

Initially the /var/log/acpid log file reported

/usr/X11R6/bin/xset:  unable to open display ""

The same command works when I enter it as root on the command line so I changed the command to 

/usr/X11R6/bin/xset -display :0.0 dpms force off

and now I'm getting the following error.

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/usr/X11R6/bin/xset:  unable to open display ":0.0"

How do I get this to work? I could probably use xhost + but that's not going to help me if gdm is showing the logon screen.

---

### Post by xx404 on 2005-09-11
[QUOTE=xx404]I'm trying to get my LCD panel to trun off when I close the lid on my notebook. I've written the appropriate APCI scripts and they are being run when the lid is opened and closed but I'm having trouble with permissions and the xset command.

The script that is being run is in /etc/acpi/local and is owned by root and is executable. The command I am using to turn off the LCD is

/usr/X11R6/bin/xset dpms force off

Initially the /var/log/acpid log file reported

/usr/X11R6/bin/xset:  unable to open display ""

The same command works when I enter it as root on the command line so I changed the command to 

/usr/X11R6/bin/xset -display :0.0 dpms force off

and now I'm getting the following error.

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/usr/X11R6/bin/xset:  unable to open display ":0.0"

How do I get this to work? I could probably use xhost + but that's not going to help me if gdm is showing the logon screen.[/QUOTE]
 This is caused because the script does not have permission to communicate with the running X server. To solve it, the script needs to set the XAUTHORITY environment variable to the location of that .Xauthority file being used by the X server. The xset command then uses that to authenticate itself with the X server so that it has permissions to issue the appropriate commands. Below is the script that is invoked by acpid when the lid is opened and closed. This works both when a user is logged on and when the gdm greeter is being displayed.

#!/bin/sh
LIDSTATE='/tmp/acpi-lidstate'
#You can also dynamically determine DISPLAY and XAUTHORITY values by looking in /proc/[PID]/environ
MONITOR='/usr/X11R6/bin/xset -display :0 dpms force'
export XAUTHORITY=/var/lib/gdm/:0.Xauth

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        $MONITOR off
        ifdown wlan0
        echo `fgconsole` > $LIDSTATE
else
        # Changing to another terminal and then back to the X server wakes it up.
        chvt 12
        chvt `cat $LIDSTATE`
        ifup wlan0
fi

---

### Post by insaneidiot on 2007-10-31
Where do I put that script?  I'm running Gutsy and my screen won't blank when it's closed either.

---

### Post by stchman on 2007-10-31
> **xx404 said:**
> I'm trying to get my LCD panel to trun off when I close the lid on my notebook. I've written the appropriate APCI scripts and they are being run when the lid is opened and closed but I'm having trouble with permissions and the xset command.

The script that is being run is in /etc/acpi/local and is owned by root and is executable. The command I am using to turn off the LCD is

/usr/X11R6/bin/xset dpms force off

Initially the /var/log/acpid log file reported

/usr/X11R6/bin/xset:  unable to open display ""

The same command works when I enter it as root on the command line so I changed the command to 

/usr/X11R6/bin/xset -display :0.0 dpms force off

and now I'm getting the following error.

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/usr/X11R6/bin/xset:  unable to open display ":0.0"

How do I get this to work? I could probably use xhost + but that's not going to help me if gdm is showing the logon screen.

All you need to do is go to Preferences--->Power Management and there is a section on what to do when the lid is closed on either AC or battery.  You can select black screen.

---

### Post by insaneidiot on 2007-10-31
I've set it to blank the screen when using A/C and battery power but it still does nothing.

---

### Post by stchman on 2007-11-01
> **insaneidiot said:**
> I've set it to blank the screen when using A/C and battery power but it still does nothing.

When I close my Toshiba lid the screen goes black.

---

### Post by insaneidiot on 2007-11-01
Well I have a Dell with an ATI Mobility Radeon X1400.  I'm thinking it's a driver problem as ATI has poor open source driver support.  What GPU do you have in your Toshiba?

---

