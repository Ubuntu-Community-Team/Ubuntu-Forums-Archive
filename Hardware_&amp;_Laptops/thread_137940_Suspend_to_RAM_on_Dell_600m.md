---
title: "Suspend to RAM on Dell 600m"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by akniss on 2006-02-28
I have gotten suspend to RAM working through the logout menu.  It works great.  However, the suspend button on my Dell inspiron 600m is not working.  I have a sleepbtn event when pressing Fn+Esc:
```
akniss@Dell_Laptop:~$ acpi_listen
button/sleep SBTN 00000080 00000001
button/sleep SBTN 00000080 00000002
button/sleep SBTN 00000080 00000003
button/sleep SBTN 00000080 00000004

```
But when I press Fn+Esc, nothing happens.  The contents of /etc/acpi/sleep.sh are:
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

Anyone know why I can suspend using the logout menu, but nothing happens when I use the suspend button?

---

### Post by ranf on 2006-03-01
Post your `/etc/acpi/events/sleepbtn' file please.

---

### Post by akniss on 2006-03-01
[QUOTE=ranf]Post your `/etc/acpi/events/sleepbtn' file please.[/QUOTE]

```
# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

event=button[ /]sleep
action=/etc/acpi/sleep.sh

```

>>EDIT: removed the /etc/acpi/sleep.sh contents, which I already posted above.

---

### Post by ranf on 2006-03-02
[QUOTE=akniss]```
# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

event=button[ /]sleep
action=/etc/acpi/sleep.sh

```
[/QUOTE]

Try adding sleep behind sleep.sh:
```
action=/etc/acpi/sleep.sh sleep

```

---

### Post by akniss on 2006-03-02
[QUOTE=ranf]Try adding sleep behind sleep.sh:
```
action=/etc/acpi/sleep.sh sleep

```[/QUOTE]

That did it!!!  Thank you so much!  Such a simple solution to a problem that's been irking me for two months!  \\:D/

---

