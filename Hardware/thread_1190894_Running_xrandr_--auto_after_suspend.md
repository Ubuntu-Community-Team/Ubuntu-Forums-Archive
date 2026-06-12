---
title: "Running xrandr --auto after suspend"
date: 2009-06-18
forum: Hardware
---

### Post by dro0g on 2009-06-18
I frequently dock/undock my laptop. When docked, the lid is closed and I can't see the built in screen or access the keyboard. I rarely shutdown between docking and undocking, the laptop is generally in suspend which means the external monitor isn't automatically detected.

Right now I hit the power button to resume, wait a few seconds and type my screensaver password in, wait a few more seconds and hit ALT-F2, type gnome-terminal and hit enter, wait a few seconds and type xrandr --auto and hit enter. If all goes well, X is now displaying on the external screen.

I've been trying to get xrandr --auto to run automatically after coming out of suspend. I created a script in /etc/acpi/resume.d but it doesn't seem to execute:

```

#!/bin/bash
export DISPLAY=:0
export XAUTHORITY=/home/username/.Xauthority
xrandr --auto

```

Is this even the correct place to put something to run after suspend or should it be in /etc/pm/sleep.d? What's the reason behind those two different directories (is one depreciated or something?) Any other ideas for enabling automatic display switching? I've tried getting the screen hotkey working on an external keyboard but the issue I ran into was that it doesn't seem to be allowed when the screen is locked.

---

### Post by sdennie on 2009-06-18
You'll need to use /etc/pm/sleep.d.  /etc/acpi/resume.d is no longer used but comes with the configuration files for acpid.  /etc/pm/sleep.d is also a bit different.  You'll need to use a script like this instead:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    ;;
    thaw|resume)
    **Your stuff here**
    ;;
    *)
    ;;
esac

exit 

```

---

### Post by dro0g on 2009-06-18
Thanks, I just tested it and it worked great!

Just for anyone else's reference, here's the final script I created in /etc/pm/sleep.d. Make sure you set home dir correctly and run 'chmod 755 <filename>' to set the script executable. 

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    ;;
    thaw|resume)
    	export DISPLAY=:0
	export XAUTHORITY=/home/username/.Xauthority
	xrandr --auto
    ;;
    *)
    ;;
esac

exit

```

---

### Post by swissz on 2011-01-26
Hi!

Thank you! It is working great! I've been looking for this for a long time. 

I extended the script, it checks whether an external VGA display is attached to the laptop, if yes, it switches exclusively to the external screen, while there is no screen attached to the VGA port, the LCD of the laptop will be active.

Here is my /etc/pm/sleep.d/switch_display :

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    ;;
    thaw|resume)
        export DISPLAY=:0
        export XAUTHORITY=/home/user/.Xauthority
        xrandr --auto
        if (xrandr -q|grep VGA|egrep -v disconnected)
          then xrandr --output LVDS1 --off
        fi
    ;;
    *)
    ;;
esac

exit

---

