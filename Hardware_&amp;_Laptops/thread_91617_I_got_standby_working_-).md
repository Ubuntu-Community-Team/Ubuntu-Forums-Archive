---
title: "I got standby working :-)"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by dskloet on 2005-11-17
Hi,

I just installed breezy on my laptop (Fujitsu Siemens Lifebook S6120) and suspend to memory is working! I guess the developers would like to know this but I don't know where to report it.

Btw, when I close the lid after going standby the fan makes some noise but I believe it stays standby. When I open the lid the laptop powers up again. Is there any way to let the lid have no effect on standby? (no noise on closing and no power up on opening)

thanks,
David

---

### Post by strawman on 2005-11-22
Did you do anything special to get suspend working?  Judging by how many posts 
concern suspend/hibernate issues, maybe you could post your work;)

---

### Post by dskloet on 2005-11-22
No, standby worked out of the box. But I wanted the power button to make it go standby for which I had to do some work. I had to edit **/etc/acpi/events/powerbtn** and change the last line to
action=/etc/acpi/sleep.sh

But then my laptop went straight to sleep again after I woke it up with the power button so I had to add this line to the top of **/etc/acpi/sleep.sh**:
[ -f /var/lock/acpisleep ] && exit 0


By the way, while my laptop is asleep the optical mouse keeps emitting the red light. Is this normal?

---

### Post by quietglow on 2005-11-22
No it shouldn't do that if its asleep. Did it have a blinking "sleep indicator" light in windows? Is that coming on?

---

### Post by dskloet on 2005-11-22
I checked with windows and it has the same blinking lightning in the display next to the keybord. **But** in windows the optical mouse also keeps emitting light during standby mode :confused: . The only difference with windows seems to be that in ubuntu, when I close the lid in standby mode, the fan makes some noise for one second and when I open the lid the laptop wakes up. In windows the lid has no effect on standby mode (which I prefer). Any thoughts on that?

---

### Post by strawman on 2005-11-22
If it's a USB mouse, then it would stay lit; my does even in standby mode.

---

### Post by quietglow on 2005-11-22
What do ya' know? So does mine!

You can do more editing on the hibernate.sh script to unlink the "wake" command from the lid button. If you need help doing this, I can give it a shot. I don't use suspend to ram (I wish I could!) but my suspend to disk only wakes when you press the power button.

---

### Post by dskloet on 2005-11-23
Yes, it's USB.

My laptop doesn't wake up on the lid button when suspended to disk either, it only does with suspend to ram. The sleep.sh I use is the standard breezy script except that I added the third line:
```

#!/bin/bash

[ -f /var/lock/acpisleep ] && exit 0

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

If you can help me that would be great.

---

