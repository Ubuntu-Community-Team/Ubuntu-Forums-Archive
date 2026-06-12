---
title: "Screen blank on lid close stopped working"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by akniss on 2005-12-16
I'm not sure what I did, but I can't seem to get the screen to go blank on lid close anymore on my Dell Inspiron 600m.

I have a lid event:
```

akniss@ubuntu:~$ acpi_listen
button/lid LID 00000080 00000005
button/lid LID 00000080 00000006
button/lid LID 00000080 00000007
button/lid LID 00000080 00000008

[1]+  Stopped                 acpi_listen

```

I don't know if this is related, but I think it started happening at the same time. On boot, the old brown background shows up on my desktop instead of my chosen background. If I go to System>Preferences>Desktop Background I can change it back to the desired bg.

/etc/acpi/lid.sh looks normal:
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

/etc/acpi/events/lidbtn Containsthe following, which I believe is correct:
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```


I think I was trying to get my computer to sleep on lid close when I noticed that it would not blank the screen anymore when I reverted back to the lid.sh from sleep.sh.  It was also around the time I was installing and playing around with kubuntu-desktop and xubuntu-desktop.  

Any ideas on what to try to get my screen to go blank on lid close again?

---

### Post by ranf on 2005-12-17
Your lid.sh looks like the original sleep.sh.
You could reinstall the package `acpi-support'.

---

### Post by akniss on 2005-12-17
[QUOTE=ranf]Your lid.sh looks like the original sleep.sh.
You could reinstall the package `acpi-support'.[/QUOTE]

That sounds like a good plan... i'll give it a try.

---

### Post by akniss on 2005-12-17
Reinstalling all the acpi packages has done me no good.  I tried deleting lid.sh then reinstalling the acpi packages again, thinking that would replace the file with the correct one... but that did not work.  So I have mad no progress on my problem.  Any one have any ideas?

---

### Post by akniss on 2005-12-17
So the screen is now going blank again when I shut the lid as it is supposed to.  I had to mark all the acpi packages AND the ubuntu-desktop package for complete removal, then reinstalled the ubuntu-desktop (which reinstalled the acpi support).  Now that problem is solved.  I am still not able to save the changes on my desktop background, but I will start a new thread, as the problems are apparently unrelated.

---

