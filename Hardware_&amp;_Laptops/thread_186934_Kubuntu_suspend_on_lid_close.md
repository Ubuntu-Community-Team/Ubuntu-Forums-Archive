---
title: "Kubuntu suspend on lid close"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by compaqdrew on 2006-06-02
Hey guys.   I'm having trouble getting KDE/Kubuntu to read my lid close events, and I'm new to linux and have absolutely no idea where to start.

Right-clicking on the battery icon in the tray and clicking 'suspend' works fine.

However, any options I set in Kubuntu's 'laptops & power' panel has absolutely no effect.  This includes changing the lid switch to "suspend".  

Also, running sleep.sh while KDE is loaded has no effect.  I have no idea why this is.

Here's my sleep.sh:
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs
. /usr/share/acpi-support/policy-funcs

DeviceConfig;

if [ x$ACPI_SLEEP != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# If gnome-power-manager or klaptopdaemon are running, let them handle policy
if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi

if [ x$LOCK_SCREEN = xtrue ]; then
    if pidof xscreensaver > /dev/null; then 
	for x in /tmp/.X11-unix/*; do
	    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	    getXuser;
	    if [ x"$XAUTHORITY" != x"" ]; then	    
		export DISPLAY=":$displaynum"
		. /usr/share/acpi-support/screenblank
	    fi
	done
    fi
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 0 /dev/hda
fi

echo -n $ACPI_SLEEP_MODE >/sys/power/state

if [ x$RESET_DRIVE = xtrue ] && [ -b /dev/hda ]; then
    hdparm -w /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -d 1 /dev/hda
fi

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/resume.sh
```

Here's my lid.sh:
```

#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-supportg
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

Any thoughts?

---

### Post by J0Sb31R on 2006-06-02
I'm having exactly the same problem with the gnome power manager... i can go to suspend or hibernate manualy but nothing happens when closing the lid...

Anyone?

hmmm i found that when restarting gdm everyting works fine.. verry wierd but no solid sollution :(

---

### Post by compaqdrew on 2006-06-02
Restarting GDM doesn't do anything for me.

Lid switch works under GNOME, not under KDE.  :(

---

### Post by jchau on 2006-09-30
> **compaqdrew said:**
> Restarting GDM doesn't do anything for me.

Lid switch works under GNOME, not under KDE.  :(

The default lid.sh tries to use some X related command to turn off the screen.  You can try this script on this thread instead (it won't put ur computer into sleep mode thoug).  [http://ubuntuforums.org/showthread.php?t=134319](http://ubuntuforums.org/showthread.php?t=134319)

About: [QUOTE=compaqdrew]Also, running sleep.sh while KDE is loaded has no effect. I have no idea why this is.
[/QUOTE]
That won't do anything when KDE is running because this line tells it to do nothing when klaptopdaemon is running:

```
# If gnome-power-manager or klaptopdaemon are running, let them handle policy
if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi
```

if u want the script to do anything with KDE running, u can just remove that line.

---

