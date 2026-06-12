---
title: "Resume from suspend failure via lid-open (Inspiron 4150)"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by linuxguiri on 2006-02-14
Any ideas on why my screen is garbled after I resume from suspend by opening the lid of my Inspiron 4150 notebook?

And/or any ideas on why I can't suspend via lid-close?

Suspend (and hibernate) works from log-out menu and resume works via powerbutton as long as I don't close the lid. 

But when I close the lid (after suspending from the log-out menu) and later open the lid, the system resumes but the video output is garbled and sometimes a large square mouse cursor appears and I have to powerdown and reboot.

I also can't suspend by just closing the lid. Screen turns off and locks, but the system doesn't suspend.

I feel so close, since suspend and hibernate work, but it would be nice to be able to close the lid after suspending.

Details:
Ubuntu Breezy 5.10
Dell Inspiron 4150 notebook
ATI Radeon 7500 Mobility video

/etc/default/acpi-support settings:

```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST=""
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
USE_DPMS=false
# RADEON_LIGHT=true
# DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
# DISABLE_DMA=true
# RESET_DRIVE=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=true

```

/etc/acpi/resume.sh contents:
```
#!/bin/bash

# Post the video card
if [ x$POST_VIDEO = xtrue ]; then
  vbetool post
fi

# Attempt to restore some video card state
if [ x$SAVE_VBE_STATE = xtrue ]; then
  vbetool vbestate restore <$VBESTATE
fi

# Now source everything in /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
  . $SCRIPT
done

# Increase the firmware loading timeout while we're doing this
# Otherwise, swap thrash tends to lead to failure to start
if [ -f /sys/class/firmware/timeout ]; then
    timeout=`cat /sys/class/firmware/timeout`
    echo 100 >/sys/class/firmware/timeout
fi

# Load any drivers that we removed
for x in $MODULES; do
    modprobe $x;
#run ifrename so that the interfaces are the same as previously
    ifrename
done

# And reset the firmware timeout
if [ -f /sys/class/firmware/timeout ]; then
    echo $timeout >/sys/class/firmware/timeout
fi

# Get PCMCIA cards back
cardctl insert

# Restart IR if necessary
if [ -f /var/run/irdadev ] && [ x$RESTART_IRDA = xtrue ]; then
    rm /var/run/irdadev;
    /etc/init.d/irda-setup start;
    /etc/init.d/irda-utils start;
fi;

# Bring up the interfaces (this should probably be left up to some policy
# manager, but at the moment we just bring back whatever we ifdowned)
#for x in $INTERFACES; do
#    ifup $x;
#done

# Actually, we don't for the moment - we end up waiting for things to time out
# because multiple ifups want to write to the state file and it's locked. We
# need a better way of doing this - for now just bring back up whatever is
# flagged as auto

ifup -a &

# Reset the time
hwclock --hctosys

# And make sure that the screen is on
if [ x$USE_DPMS = xtrue ]; then
  vbetool dpms on
fi

# Make sure that the drive power state is set correctly again
rmmod ac
modprobe ac
rmmod battery
modprobe battery
/etc/acpi/power.sh

# Some hardware needs another X/console switch in order to bring stuff back
chvt $CONSOLE;
if [ x$DOUBLE_CONSOLE_SWITCH = xtrue ]; then
  chvt 12;
  chvt $CONSOLE;
fi

# now, we should poke xscreensaver so you get a dialog
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
	su $user -c "(xscreensaver-command -deactivate)"
    fi
done

# we need to restart our services after the network is back
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x start
done

# Some hardware gets unhappy about button events unless we do this
rmmod button
modprobe button

# Kick the fans
rmmod fan
rmmod thermal
modprobe fan
modprobe thermal

if [ "`grep ibm_acpi /proc/modules`" ]; then
    # No, I don't know why
    rmmod ibm-acpi
    modprobe ibm-acpi
fi

# NNGH FAN HATE
for x in /proc/acpi/fan/*; do
    if [ "`grep on $x/state`" ]; then
	echo -n 3 > $x/state;
	echo -n 0 > $x/state;
    fi
done

#Let acpid process events again
(sleep 5 && rm /var/lock/acpisleep)&

```

/etc/acpi/lid.sh contents:
```

#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

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
                su $user -c "xscreensaver-command -unthrottle"
		
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    su $user -c "xscreensaver-command -deactivate"
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

/etc/acpi/sleep.sh contents:
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs

DeviceConfig;

if [ x$ACPI_SLEEP != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# If PowerManager is running, let it handle policy
if [ "`pidof PowerManager`" ] && [ x$1 != xforce ] && [ x$1 != xsleep ]; then
    exit;
fi

if [ x$LOCK_SCREEN = xtrue ]; then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then	    
	    export DISPLAY=":$displaynum"
	    . /usr/share/acpi-support/screenblank
	fi
    done
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$RADEON_LIGHT = xtrue ]; then
    # Some Radeons are a bit funny
    [ -x /usr/sbin/radeontool ] && radeontool light off
fi

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

---

### Post by hizaguchi on 2006-04-01
I have the same problem.  This site has some reccomendations.  [http://lists.debian.org/debian-laptop/2002/11/msg00476.html](http://lists.debian.org/debian-laptop/2002/11/msg00476.html)

---

### Post by hizaguchi on 2006-04-08
Oh yeah!  It's working!  Woohoo!

Err, ok, here's what you do:

Edit your /boot/grub/menu.list and add "acpi=off apm=on" to the end of the "kernel" line that matches what you're booting from.  Then reboot, of course.

Now it will suspend and wake back up, but everything will be frozen.  The workaround I'm using for this is to hit "ctrl-alt-F1" to go to a terminal before you suspend.  Then you can suspend and when you wake back up the terminal will be kinda stuck, but you can hit "ctrl-alt-F7" to get back to X and everything seems to work just fine.

Much thanks to the guy that wrote this page: [http://www.collinstarkweather.com/local/dellgentoowireless#](http://www.collinstarkweather.com/local/dellgentoowireless#)
for the solution... though I don't have the mouse problem he describes.

---

### Post by hizaguchi on 2006-04-09
Update:  Like the first page I linked to says, after suspending for a while, when you resume the fan will stay on constantly.  Hitting "Fn-z" fixes it.

---

### Post by linuxguiri on 2006-06-22
Hizaguchi,

Well, I've finally gotten around to trying apm instead of acpi. I got the same results. I can suspend from console but not from x windows.

I've posted a bug for the acpi-support here: [https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/31425/+index](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/31425/+index)

Since you have the same laptop and experienced the same problem, would you mind following that link and confirming the bug please?

Thanks!

---

### Post by hizaguchi on 2006-07-08
Sure.  Also, not sure if you've tried Xgl yet, but it seems that suspending from inside the Xgl server results in a nice hard lock.

---

### Post by linuxguiri on 2006-07-08
thanks, hizaguchi!

---

### Post by linuxguiri on 2006-10-21
Strangely, I was able to temporarily resume successfully about 4 times after rebooting each time (suspend never worked a second time until the machine was rebooted) after changing /etc/default/acpi-support options to:

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
# MODULES_WHITELIST="radeon"
SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=true
# SAVE_VIDEO_PCI_STATE=true
# USE_DPMS=true
# RADEON_LIGHT=true
DOUBLE_CONSOLE_SWITCH=true
# HIBERNATE_MODE=shutdown
# LOCK_SCREEN=true
# DISABLE_DMA=true
# RESET_DRIVE=true
# STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false

Current status: video garbled after resume from suspend
Why did it work 4 times and then stop?!](*,)

---

