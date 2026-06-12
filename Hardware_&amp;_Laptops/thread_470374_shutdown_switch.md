---
title: "shutdown switch"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2007-06-10
I asked this question a few months ago, but I've forgotten the answer.

I want to add a parameter to the bold line.  something like shutdown **-h now**

thanks,
CH

[I]#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs

if [ x$ACPI_HIBERNATE != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# Unset video posting - it's not needed for suspend to disk
unset POST_VIDEO
unset USE_DPMS

. /etc/acpi/prepare.sh

#if [ x$LOCK_SCREEN = xtrue ]; then
#    for x in /tmp/.X11-unix/*; do
#	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#	getXuser;
#	if [ x"$XAUTHORITY" != x"" ]; then
#	    export DISPLAY=":$displaynum"
#	    . /usr/share/acpi-support/screenblank
#	fi
#    done
#fi

echo -n $HIBERNATE_MODE >/sys/power/disk

if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
	. /etc/usplash.conf
	/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
	/sbin/s2disk $DEVICE
    fi
else
    **echo -n "disk" >/sys/power/state**
fi

$LAPTOP_MODE stop

. /etc/acpi/resume.sh[/I]

---

### Post by 444 on 2007-06-10
So you want it to shutdown instead of hibernate?

Quick and dirty:
```

#!/bin/sh
shutdown -h now
exit
... the rest is irrelevant as exit causes it to not be run

```

Course you could just save a copy of the file and make a new one with just shutdown in it. Plus there's probably an upstream script that decides which script to run in the first place...

---

