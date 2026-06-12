---
title: "resume from sleep/suspend?"
date: 2008-08-28
forum: Hardware
---

### Post by cl0ckwork on 2008-08-28
having issues with the sleep funtion on hardy. say i leave my laptop running over night and come back to it the next morning, its in the sleep mode. when i try to wake it, i can tell that the computer has responded (hdd noise, blinking LEDs) but the screen remains blacked out.

i have an nVidia GeForce 6150 is that helps at all

---

### Post by enos76 on 2008-09-20
I had the same issue with different hardware.

In my case, switching between text and graphic mode restored the image. I could finally avoid the problem by commenting a line in one of the scripts in /etc/acpi (I don't remember which one, sorry).

Good luck

-- 
enos76

---

### Post by cl0ckwork on 2008-09-21
i can restore it if i ctrl-alt-backspace to log out but it just seems very inconveinent

---

### Post by decoherence on 2008-09-21
same here. i'll try ctrl alt f1 then alt f7 next time, tho.

ADD: yep, that works for me too!

---

### Post by admelfo on 2008-10-04
> **decoherence said:**
> same here. i'll try ctrl alt f1 then alt f7 next time, tho.

Huh. I tried this and it worked -- took me to a non-GUI screen that asked for a log-in, but it let me back into the Ubie desktop just by hitting return.

Looking forward to trying alt-f7 next time just to see what it does.

Thanks.

---

### Post by svivian on 2008-10-06
> **enos76 said:**
> In my case, switching between text and graphic mode restored the image. I could finally avoid the problem by commenting a line in one of the scripts in /etc/acpi (I don't remember which one, sorry).

Is it possible for you to find out somehow, eg by looking in that folder? This is annoying me. Though at least the Ctrl+Alt+F7 solution does work :)

---

### Post by cl0ckwork on 2008-10-06
here is my /etc/acpi/lid.sh file

i have a feeling something in this one should be the solution

```
#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

unfortunately i am better versed in C++ than in bash scripting, hopefully someone can make sense out of this

EDIT: here is the etc/default/acpi-support file that i was fiddling with
```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12
```

---

